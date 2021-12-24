## IOS

## deep link 관련
https://developers.helpshift.com/unity-4x/deep-linking-ios/

https://leedeokho.github.io/2018/05/29/URLSchemes

## react-native npm run ios error
### RN Typedef redefinition with different types ('uint8_t' (aka 'unsigned char') vs 'enum clockid_t') error

<!-- podfile -->
```
require_relative '../node_modules/react-native/scripts/react_native_pods'
require_relative '../node_modules/@react-native-community/cli-platform-ios/native_modules'

platform :ios, '11.0'

target 'ReactNativeApp' do
  config = use_native_modules!

  use_react_native!(
    :path => config[:reactNativePath],
    # to enable hermes on iOS, change `false` to `true` and then install pods
    :hermes_enabled => false
  )

  target 'ReactNativeAppTests' do
    inherit! :complete
    # Pods for testing
  end

  # Enables Flipper.
  #
  # Note that if you have use_frameworks! enabled, Flipper will not work and
  # you should disable the next line.
  use_flipper!()

  post_install do |installer|
    react_native_post_install(installer)
    __apply_Xcode_12_5_M1_post_install_workaround(installer)
  end
end
```

### Solution
Delete the Flipper module. Delete or comment the following lines in the Podfile file. If the AppDelegate.m file also has related Flipper code, it also needs to be delete or comment.

#### flipper_pods! 부분 comment 처리
```
#  add_flipper_pods!
#  post_install do |installer|
#    flipper_post_install(installer)
#  end 
```

#### re-run pod intall.
cd ios && rm -rf Pods Podfile.lock && pod install

<!-- countermeasure url -->
https://blog.cpming.top/p/uint8-t-aka-unsigned-char-vs-enum-clock-t