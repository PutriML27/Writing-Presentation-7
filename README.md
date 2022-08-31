# React.js - Hooks
**Hooks** merupakan fitur baru di React 16.8. Dengan Hooks, kita dapat menggunakan state dan fitur React yang lain tanpa perlu menulis sebuah kelas baru sehingga bisa menggunakannya di functional component.

Terdapat 2 jenis Hooks:
1. useState

Digunakan untuk membuat dan mengupdate state. Contoh:
``` 
    import React, { useState } from 'react';

    export default function App() {
        const [state, setState] = useState('brachio');

        const handleChange = () => {
            setState('t-rex');
        };

        return (
            <div>
                <h1>Hello Devsaurus</h1>
                <p>My Name is {state}</p>
                <button onClick={handleChange}>Change Name</button>
            </div>
        );
    }
```
2. useEffect

React hooks useEffect digunakan untuk menambahkan side effect ke function komponen.
``` 
    import React, { useState, useEffect } from 'react';

    function Example() {
        const [count, setCount] = useState(0);

        // Sama seperti componentDidMount dan componentDidUpdate:
        useEffect(() => {
        // Memperbarui judul dokumen menggunakan API browser
        document.title = `Anda klik sebanyak ${count} kali`;
        });

        return (
            <div>
             <p>Anda klik sebanyak {count} kali</p>
             <button onClick={() => setCount(count + 1)}>
                Klik saya
             </button>
            </div>
        );
    }
```
**Prop Types**

merupakan sebuah library yang dapat membanatu untuk memeriksa data props agar sesuai ekspektasi, namun apabila tidak sesuai maka akan muncul pesan error.
>npm install prop-types
``` 
    import PropTypes from 'prop-types';
    function Header (props) {
        return (
            <>
                <h2>Name: {props.char}</h2>
                <h2> Age: {props.age}</h2>
            </>
        );
    };
    Header.propTypes = {
        char: PropTypes.string,
        age: PropTypes.number
    };
```
# React Router 6
Di React, router membantu membuat dan menavigasi di antara berbagai URL yang membentuk aplikasi web yang kiat buat. Mereka memungkinkan pengguna untuk berpindah diantara komponen aplikasi Anda sambil mempertahankan status pengguna, dan dapat memberikan URL unik untuk komponen ini agar lebih mudah dibagikan. 
>npm install react-router-dom@6
``` 
    import ReactDOM from "react-dom/client";
    import { BrowserRouter } from "react-router-dom";
    import App from "./App";

    const root = ReactDOM.createRoot ( 
        document.getElementById("root")
    );
    root.render(
     <BrowserRouter>
     <App />
     </BrowserRouter>
    );
```
Redux sebagai state management. Dengan menggunakan Redux maka kita cukup bikin satu state dan state itu bisa di akses di komponen manapun.

# React Redux
**Redux** adalah sebuah aplikasi state management. State management adalah cara untuk memfasilitasi komunikasi dan berbagai data lintas komponen. Ia berfungsi untuk melakukan perubahan state yang dibutuhkan oleh setiap fungsional yang ada di suatu aplikasi.
>npm install redux 
Ada 3 poin penting dalam redux :
- Store
- Reducer
- Action

1. **action** merupakan sebuah object yang memiliki property type.
``` 
    const ADD_DATA = (newData) => {
        return { type: 'ADD_DATA', data: newData }
    }
    
    export default ADD_DATA
```
2. **Reducer** adalah bagian redux yang merubah state menjadi respon yang terjadi ketika Action di dispatch().
``` 
    const initialState = { }
    const reducer = (prevState = initialState, action) => {
        if (action.type === 'ADD_DATA') {
            return { ...prevState, action.data }
        }
        return prevState
    }
    
    export default reducer
```
3. **Store** berfungsi untuk menggabungkan Action dan Reducer agar bisa bekerja sebagai state manajemen.

Store bertanggung jawab sebagai:
- menyimpan keseluruhan state.
- mengakses state dengan cara getState()
-menjalankan reducer untuk merubah state dengan cara dispatch(action).
``` 
    import { createStore } from 'redux'
    import reducer from './reducer'

    const store = createStore(reducer)

    export default store
```
