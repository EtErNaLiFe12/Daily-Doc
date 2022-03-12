## Typescript


## React + Typescript


## Context API

* need to improve

```ts
// types.ts
export type DefaultState = {
  logIn: (
    setToken: string, 
    id: string
  ) => void;
  logOut: () => void;
  isAuth: boolean;
};

export type ChildrenProps = React.PropsWithChildren<{}>;
```

```ts
//AuthPrivider.tsx
import { createContext, useEffect, useState } from "react";
import { useNavigate } from "react-router-dom";
import { ChildrenProps, DefaultState } from '../types/types';

// interface User {
//   ///
// }

const defaultContextVal : DefaultState = {
  logIn: () => {},
  logOut: () => {},
  isAuth: false,
  // user: User
}

export const AuthContext = createContext<DefaultState>(defaultContextVal);

const AuthProvider = ({ children }: ChildrenProps) => {

  const navigate = useNavigate();
  const [isAuth, setIsAuth] = useState<boolean>(false);
  
  const authCheck = async () => {

    // check token
      // if token -> fetch profile
        // logic

    const authToken = sessionStorage.getItem('token')
    if(authToken) {
      setIsAuth(true)
    } else {
      setIsAuth(false)
    }  
  }
  
  useEffect(() => {
    authCheck();
  }, []);

  const logIn = (setToken: string, userId: string) => {
    setIsAuth(true);
    sessionStorage.setItem('token', setToken)
    sessionStorage.setItem('id', userId)
  };

  const logOut = () => {
    setIsAuth(false);
    sessionStorage.removeItem('token')
    sessionStorage.removeItem('id')
    console.log('token, id 삭제')
    navigate("/login")
  }

  return (
    <AuthContext.Provider value={{logIn, logOut, isAuth}}>
      {children}
    </AuthContext.Provider>
  )
}

export default AuthProvider;
```



```ts
// usage
  const { logIn } = useContext(AuthContext);
```
