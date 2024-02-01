# 6 useState mistake

<details>
      <summary>
        # Mistake 1
     </summary>

```javascript
import React from 'react'
import { useState } from 'react'

const Number = () => {

    const [number , setNumber] = useState(0)

    const increase = () => {

        setNumber(number+1)
    }

    const increaseAsync= () => {

        setTimeout(() => {
            setNumber(number+1)

        } , 2000)


    }

  return (
    <div>
        <h1>{number}</h1>
        <button onClick={increase}>Increase</button>
        <button onClick={increaseAsync}>Increase Async</button>

    </div>
  )
}

export default Number




// Problem solve



import React from 'react'
import { useState } from 'react'

const Number = () => {

    const [number , setNumber] = useState(0)

    const increase = () => {

        setNumber(number+1)
    }

    const increaseAsync= () => {

        setTimeout(() => {
            setNumber((prev) => prev+ 1)

        } , 2000)


    }

  return (
    <div>
        <h1>{number}</h1>
        <button onClick={increase}>Increase</button>
        <button onClick={increaseAsync}>Increase Async</button>

    </div>
  )
}

export default Number
```

</details>
<details>
      <summary>
       Mistake 2
     </summary>

```javascript
// ????????  Problem Blank page   with empty user list ???????

import React from 'react'
import { useState } from 'react'

const First = () => {

   const [user ,setUser] =useState()

  return (
    <div>
      <span>User name : {user.name} </span>
    </div>
  )
}

export default First

//?????  solve it many ways    First Way  ???????

import React from 'react'
import { useState } from 'react'

const First = () => {

   const [user ,setUser] =useState()

  return (
    <div>
      <h2>User</h2>
      <span>User name : {user?.name} </span>
    </div>
  )
}

export default First

//?????    Second  Way   ???????

import React from 'react'
import { useState } from 'react'

const First = () => {

   const [user ,setUser] =useState({})

  return (
    <div>
      <h2>User</h2>
      <span>User name : {user.name} </span>
    </div>
  )
}

export default First

//????? sometime    Second  Way  not Enough It create problem  for Example   ???????

import React from 'react'
import { useState } from 'react'

const First = () => {

   const [user ,setUser] =useState({})

  return (
    <div>
      <h2>User</h2>
      <span>User name : {user.name} </span>
      <span>User Profile picture  : {user.images[0]} </span>
    </div>
  )
}

export default First

// Problem solving Using     username :"" , email:"",  image :[]

import React from 'react'
import { useState } from 'react'

const First = () => {

  const [user ,setUser] =useState({
    username :"" ,
    email:"",
    image :[]
   })

  return (
    <div>
      <h2>User</h2>
      <span>User name : {user.name} </span> <br />
      <span>User Profile picture  : {user.image[1]} </span>
    </div>
  )
}

export default First

// Change input user

import React from "react";
import { useState } from "react";

const First = () => {
  const [input, setInput] = useState("");

  const [user, setUser] = useState({
    name: "john",
    email: "john@gmail.com",
    image: ["profile.pic", "banner.png"],
  });

  const changeUser = () => {
    setUser((prev) => ({ ...prev, name: input }));
  };

  return (
    <div>
      <h2>User</h2>
      <input
        onChange={(e) => setInput(e.target.value)}
        type="text"
        placeholder="Type username...."
      />
      <button onClick={changeUser}>Change username </button>
      <p>User name : {user.name} </p>
    </div>
  );
};

export default First;

```

</details>
<details>
      <summary>
       Mistake 3
     </summary>

```javascript
import React, { useState } from "react";

const ChangeUser = () => {
  const [user, setUser] = useState({
    name: "",
    surname: "",
    username: "",
    email: "",
    password: "",
    country: "",
    city: "",
    address: "",
  });

  const handleChange = (e) => {
    setUser((prev) => ({ ...prev, [e.target.name]: e.target.value }));
  };

  console.log(user);

  return (
    <div>
      <form className="row g-3 fs-2">
        <input
          type="text"
          name="name"
          onChange={handleChange}
          placeholder="name"
        />
        <input
          type="text"
          name="surname"
          onChange={handleChange}
          placeholder="surname"
        />
        <input
          type="text"
          name="username"
          onChange={handleChange}
          placeholder="username"
        />
        <input
          type="text"
          name="email"
          onChange={handleChange}
          placeholder="email"
        />
        <input
          type="text"
          name="password"
          onChange={handleChange}
          placeholder="password"
        />
        <input
          type="text"
          name="country"
          onChange={handleChange}
          placeholder="country"
        />
        <input
          type="text"
          name="city"
          onChange={handleChange}
          placeholder="city"
        />
        <input
          type="text"
          name="address"
          onChange={handleChange}
          placeholder="address"
        />
      </form>
      <p>Name :{user.name} </p>
      <p>surname :{user.surname} </p>
      <p>username :{user.username} </p>
      <p>Email: {user.email} </p>
      <p>Password: {user.password} </p>
      <p>Country: {user.country} </p>
      <p>city: {user.city} </p>
      <p>Address: {user.address} </p>
    </div>
  );
};

export default ChangeUser;
```

</details>
<details>
      <summary>
       Mistake 4
     </summary>

```javascript
import React, { useState } from "react";

const Form = () => {
  const [product, setProduct] = useState({
    title: "",
    desc: "",
    price: "",
    category: "",
    tags: [],
    images: {
      sm: "",
      md: "",
      lg: "",
    },
    quantity: 0,
  });

  return (
    <div>
      <form className="row g-3 fs-2">
        <input type="text" placeholder="Title" />
        <input type="text" placeholder="Desc" />
        <input type="number" placeholder="Price" />
        <p>Category:</p>
        <select name="cars" id="cars">
          <option value="sneakers">Sneakers</option>
          <option value="tshirts">T-Shirt</option>
          <option value="jeans">Jeans</option>
        </select>
        <p>Tags:</p>
        <textarea name="" id="" cols="5" rows="5"></textarea>
      </form>
      <br />
      <button className="btn btn-dark fs-1">-</button>{" "}
      <span className="fs-1"> Quatity(0)</span>{" "}
      <button className="btn btn-dark fs-1">+</button>
    </div>
  );
};

export default Form;
```

</details>
<details>
      <summary>
        Mistake 5 
     </summary>

```javascript

// Problem Create this


import { useState } from "react"
import React  from 'react'

const Mistake_5 = () => {

    const [products, setProducts] = useState([
        {id:1 , title: 'black snekers' ,  quantity: 1},
        {id:2 , title: 'red  T-shirts' ,  quantity: 1},
        {id:3 , title: 'blue jeans' ,  quantity: 1},

      ])

      const[selectedProduct, setSelectedProduct] = useState({})

    const increment = (id) => {
      setProducts((prev) => {
        return prev.map((product) => {
          if(product.id===id){
           return {...product, quantity: product.quantity+1}
          }else return product
        })

      })
    }

    const handleChoose = (id) => {
     const product=  products.find((p) => p.id===id)
      setSelectedProduct(product)
    }
  return (
    <div>
        <h4>All Products </h4>
      {products.map((product) => (

        <div key={product.id}>
         <span>{product.title}
          <button onClick={() => handleChoose(product.id)}> Choose </button>
         </span>
         <div>
          <button>-</button>
          <span> {product.quantity}</span>
          <button onClick={() => increment(product.id)}>+</button>
         </div>

        </div>
      ))}

      <h4>Selected Product</h4>
      <span>{selectedProduct.title}</span>
      <span>{selectedProduct.quantity}</span>
    </div>
  )
}

export default Mistake_5





// Proble Solve



import React ,{useState} from 'react'

const Mistake_5 = () => {


  const [products, setProducts] = useState([
    {id:1 , title: 'black snekers' ,  quantity: 1},
    {id:2 , title: 'red  T-shirts' ,  quantity: 1},
    {id:3 , title: 'blue jeans' ,  quantity: 1},

  ])

  const[selectedId, setSelectedId] = useState(null)

  const selectedProduct = products.find((p) => p.id===selectedId)

const increment = (id) => {
  setProducts((prev) => {
    return prev.map((product) => {
      if(product.id===id){
       return {...product, quantity: product.quantity+1}
      }else return product
    })

  })
}

const handleChoose = (id) => {
  setSelectedId(id)
}

  return (
    <div>

     <h4>All Products </h4>
      {products.map((product) => (

        <div key={product.id}>
         <span className='fs-1'>{product.title}
          <button onClick={() => handleChoose(product.id)}> Choose </button>
         </span>
         <div className='quantity'>
          <button className='fs-1 btn btn-dark '>-</button>
          <span className='fs-1'>{product.quantity}</span>
          <button className='fs-1 btn btn-dark m-3' onClick={() => increment(product.id)}>+</button>
         </div>

        </div>
      ))}

      <h4 className='fs-1'>Selected Product</h4>
      <span className='fs-1'>{selectedProduct?.title}</span>
      <span className='fs-1 m-3'>{selectedProduct?.quantity}</span>

    </div>
  )
}

export default Mistake_5
```

</details>

</br>

# useEffect

<details>
      <summary>
       Mistake 1
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";

function App() {
  const [number, setNumber] = useState(0);

  console.count("Component renders");

  return (
    <div>
      <span>You Clicked {number} times </span>

      <button onClick={() => setNumber((prev) => prev + 1)}> Increase </button>
    </div>
  );
}

export default App;



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home





import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts




```

</details>
<details>
      <summary>
       Mistake 2 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.count("Effect runs");
    document.title = `You Clicked ${number} times  `;
  });

  console.count("Component renders");

  return (
    <div>
      <span>You Clicked {number} times </span>

      <button onClick={() => setNumber((prev) => prev + 1)}> Increase </button>
    </div>
  );
}

export default App;


import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home





import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts


```

</details>

<details>
      <summary>
       Mistake 3 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";

function App() {
  const [number, setNumber] = useState(0);
  const [name, setName] = useState("");

  useEffect(() => {
    console.count("Effect runs");
    document.title = `You Clicked ${number} times  `;
  }, []);

  console.count("Component renders");

  return (
    <div>
      <span>You Clicked {number} times </span>

      <button onClick={() => setNumber((prev) => prev + 1)}> Increase </button>
      <input type="text" onChange={(e) => setName(e.target.value)} />
    </div>
  );
}

export default App;




import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home




import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts




```

</details>
<details>
      <summary>
        mistake 4 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";

function App() {
  const [number, setNumber] = useState(0);
  const [name, setName] = useState("");

  useEffect(() => {
    console.count("Effect runs");
    document.title = `You Clicked ${number} times  `;
  }, [number]);

  console.count("Component renders");

  return (
    <div>
      <span>You Clicked {number} times </span>

      <button onClick={() => setNumber((prev) => prev + 1)}> Increase </button>
      <input type="text" onChange={(e) => setName(e.target.value)} />
    </div>
  );
}

export default App;






import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home











import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts
```

</details>
<details>
      <summary>
       Mistake 5 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";

function App() {
  const [number, setNumber] = useState(0);
  const [name, setName] = useState("");

  useEffect(() => {
    console.count("Effect runs");
    document.title = `Title of the App `;
  }, []);

  console.count("Component renders");

  return (
    <div>
      <span>You Clicked {number} times </span>

      <button onClick={() => setNumber((prev) => prev + 1)}> Increase </button>
      <input type="text" onChange={(e) => setName(e.target.value)} />
    </div>
  );
}

export default App;





import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home





import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts


```

</details>
<details>
      <summary>
       Mistake 6 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";

function App() {
  const [name, setName] = useState("");

  const [state, setState] = useState({
    name: "",
    selected: false,
  });

  const handleAdd = () => {
    setState((prev) => ({ ...prev, name }));
  };

  const handleSelect = () => {
    setState((prev) => ({ ...prev, selected: true }));
  };

  return (
    <div>
      <input
        type="text"
        onChange={(e) => setName(e.target.value)}
        className="m-4 p-2"
      />
      <button onClick={handleAdd}>Add Name </button>
      <button onClick={handleSelect}>Select </button>
      {`{
        name: ${state.name} ,
        state: ${state.selected.toString()},
      }`}
    </div>
  );
}

export default App;




import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home




import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts


```

</details>
<details>
      <summary>
        useEffect has changed 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";

function App() {
  const [name, setname] = useState("");

  const [state, setState] = useState({
    name: "",
    selected: false,
  });

  useEffect(() => {
    console.log("The state has been changed  useEffect run  ");
  }, [state]);

  const addHandle = () => {
    setState((prev) => ({ ...prev, name }));
  };

  const selectHandle = () => {
    setState((prev) => ({ ...prev, selected: true }));
  };

  return (
    <div>
      <input type="text" onChange={(e) => setname(e.target.value)} />
      <button onClick={addHandle}>Add name </button>
      <button onClick={selectHandle}>Add Selected </button>

      {`{
        name: ${state.name} ,
        state: ${state.selected.toString()},
      }`}
    </div>
  );
}

export default App;




import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home



import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts
```

</details>
<details>
      <summary>
       No i solve useMemo 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";
import { useMemo } from "react";

function App() {
  const [name, setname] = useState("");

  const [state, setState] = useState({
    name: "",
    selected: false,
    age: 20,
    city: "",
  });

  const user = useMemo(
    () => ({
      name: state.name,
      selected: state.selected,
    }),
    [state.name, state.selected]
  );

  useEffect(() => {
    console.log("The state has been changed  useEffect run  ");
  }, [user]);

  const addHandle = () => {
    setState((prev) => ({ ...prev, name }));
  };

  const selectHandle = () => {
    setState((prev) => ({ ...prev, selected: true }));
  };

  return (
    <div>
      <input type="text" onChange={(e) => setname(e.target.value)} />
      <button onClick={addHandle}>Add name </button>
      <button onClick={selectHandle}>Add Selected </button>

      {`{
        name: ${state.name} ,
        state: ${state.selected.toString()},
      }`}
    </div>
  );
}

export default App;


import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home


import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts



```

</details>
<details>
      <summary>
       No 2 solve 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";
import { useMemo } from "react";

function App() {
  const [name, setname] = useState("");

  const [state, setState] = useState({
    name: "",
    selected: false,
    age: 20,
    city: "",
  });

  useEffect(() => {
    console.log("The state has been changed  useEffect run  ");
  }, [state.name, state.selected]);

  const addHandle = () => {
    setState((prev) => ({ ...prev, name }));
  };

  const selectHandle = () => {
    setState((prev) => ({ ...prev, selected: true }));
  };

  return (
    <div>
      <input type="text" onChange={(e) => setname(e.target.value)} />
      <input type="text" onChange={(e) => setname(e.target.value)} />
      <button onClick={addHandle}>Add name </button>
      <button onClick={selectHandle}>Add Selected </button>

      {`{
        name: ${state.name} ,

        state: ${state.selected.toString()},
      }`}
    </div>
  );
}

export default App;



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home




import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts


```

</details>
<details>
      <summary>
       Mistake 1 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";
import { useMemo } from "react";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.log("Effect");
    setInterval(() => {
      setNumber(number + 1);
    }, 1000);
  }, [number]);

  return (
    <div className="container text-center m-5">
      <h1>{number} </h1>
    </div>
  );
}

export default App;



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home



import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts


```

</details>
<details>
      <summary>
        mis 1 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";
import { useMemo } from "react";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.log("Effect");
    setInterval(() => {
      setNumber((prev) => prev + 1);
    }, 1000);
  }, []);

  return (
    <div className="container text-center m-5">
      <h1>{number} </h1>
    </div>
  );
}

export default App;



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home


import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts
```

</details>
<details>
      <summary>
        mis 2 
     </summary>

```javascript
import React, { useState, useEffect } from "react";
import "bootstrap/dist/css/bootstrap.min.css";

import "bootstrap/dist/js/bootstrap";
import { useMemo } from "react";

function App() {
  const [number, setNumber] = useState(0);

  useEffect(() => {
    console.log("Effect");
    setInterval(() => {
      setNumber((prev) => prev + 1);
    }, 1000);
  }, []);

  return (
    <div className="container text-center m-5">
      <h1>{number}wewess</h1>
    </div>
  );
}

export default App;


import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home


import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts
```

</details>
<details>
      <summary>
       Fetch api data 
     </summary>

```javascript
import React from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";
import Home from "./Home";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Posts from "./Posts";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/posts" element={<Posts />} />
      </Routes>
    </Router>
  );
}

export default App;



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home




import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {
    setPosts(data)
  })

  })
  return (
    <div>
        {posts?.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts

```

</details>
<details>
      <summary>
       This is problem 
     </summary>

```javascript
import React from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";
import Home from "./Home";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Posts from "./Posts";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/posts" element={<Posts />} />
      </Routes>
    </Router>
  );
}

export default App;

\



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home




import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {


      alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);

    })




  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts


```

</details>
<details>
      <summary>
      This is solve 
     </summary>

```javascript
import React from "react";
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap/dist/js/bootstrap";
import Home from "./Home";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Posts from "./Posts";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/posts" element={<Posts />} />
      </Routes>
    </Router>
  );
}

export default App;



import React from 'react'

import { Link } from 'react-router-dom'
 import Posts from './Posts'

const Home = () => {
  return (
    <div>
        <Link className="text-center" to="/posts"> Go to posts </Link>
    </div>
  )
}

export default Home



import React ,{useState ,useEffect} from 'react'



const Posts = () => {

    const [posts,setPosts] = useState([])


  useEffect(() => {


    let isCancelled = false

    fetch("https://jsonplaceholder.typicode.com/posts").then((res) => res.json()).then((data) => {

    if(isCancelled) {
          alert("Post are ready to be ,Updated!")
    setPosts(data)
    console.log(data);
      }
    })


  return () => {
    isCancelled = true
  }

  })
  return (
    <div>
        {posts.map((p) => (<p className='m-5 fs-1' key={p.id}> {p.title} </p>

        ) )}
    </div>
  )
}

export default Posts

```

</details>

</br></br>

<details>
      <summary>
        Learn useReducer 
     </summary>

```javascript
// FIRST EXAMPLE
// import Post from "./Post";
// import "./post.css";

// SECOND EXAMPLE
import Form from "./Form";
import "./form.css";

function App() {
  return (
    // FIRST EXAMPLE
    // <Post />

    // SECOND EXAMPLE
    <Form />
  );
}

export default App;




import React, { useReducer, useRef, useState } from "react";
import { formReducer, INITIAL_STATE } from "./formReducer";

const Form = () => {

  // USING USESTATE

  // const [product, setProduct] = useState({
  //   title: "",
  //   desc: "",
  //   price: 0,
  //   category: "",
  //   tags: [],
  //   images: {
  //     sm: "",
  //     md: "",
  //     lg: "",
  //   },
  //   quantity: 0,
  // });

  // const handleChange = (e) => {
  //   setProduct((prev) => ({ ...prev, [e.target.name]: e.target.value }));
  // };

  // const tagRef = useRef();

  // const handleTags = () => {
  //   const tags = tagRef.current.value.split(",");
  //   tags.forEach((tag) => {
  //     setProduct((prev) => ({ ...prev, tags: [...prev.tags, tag] }));
  //   });
  // };

  // const handleRemoveTag = (tag) => {
  //   setProduct((prev) => ({
  //     ...prev,
  //     tags: prev.tags.filter((t) => t !== tag),
  //   }));
  // };

  // const handleIncrease = () => {
  //   setProduct((prev) => ({ ...prev, quantity: prev.quantity + 1 }));
  // };

  // const handleDecrease = () => {
  //     setProduct((prev) => ({
  //       ...prev,
  //       quantity: prev.quantity - 1,
  //     }));
  // };




  //USING USEREDUCER

  const [state, dispatch] = useReducer(formReducer, INITIAL_STATE);
  const tagRef = useRef();

  const handleChange = (e) => {
    dispatch({
      type: "CHANGE_INPUT",
      payload: { name: e.target.name, value: e.target.value },
    });
  };

  const handleTags = () => {
    const tags = tagRef.current.value.split(",");
    tags.forEach((tag) => {
      dispatch({ type: "ADD_TAG", payload: tag });
    });
  };

  return (

    // USING USESTATE

    // <div>
    //   <form>
    //     <input
    //       type="text"
    //       name="title"
    //       onChange={handleChange}
    //       placeholder="Title"
    //     />
    //     <input
    //       type="text"
    //       name="desc"
    //       onChange={handleChange}
    //       placeholder="Desc"
    //     />
    //     <input
    //       type="number"
    //       name="price"
    //       onChange={handleChange}
    //       placeholder="Price"
    //     />
    //     <p>Category:</p>
    //     <select name="category" id="category" onChange={handleChange}>
    //       <option value="sneakers">Sneakers</option>
    //       <option value="tshirts">T-shirts</option>
    //       <option value="jeans">Jeans</option>
    //     </select>
    //     <p>Tags:</p>
    //     <textarea
    //       ref={tagRef}
    //       placeholder="Seperate tags with commas..."
    //     ></textarea>
    //     <button type="button" onClick={handleTags}>
    //       Add Tags
    //     </button>
    //     <div className="tags">
    //       {product.tags.map((tag) => (
    //         <small key={tag} onClick={() => handleRemoveTag(tag)}>
    //           {tag}
    //         </small>
    //       ))}
    //     </div>
    //     <div className="quantity">
    //       <button type="button" onClick={handleDecrease}>
    //         -
    //       </button>
    //       <span>Quantity ({product.quantity})</span>
    //       <button type="button" onClick={handleIncrease}>
    //         +
    //       </button>
    //     </div>
    //   </form>
    // </div>


    //USING USEREDUCER

    <div>
      <form>
        <input
          type="text"
          placeholder="Title"
          onChange={handleChange}
          name="title"
        />
        <input
          type="text"
          placeholder="Desc"
          onChange={handleChange}
          name="desc"
        />
        <input
          type="number"
          placeholder="Price"
          onChange={handleChange}
          name="price"
        />
        <p>Category:</p>
        <select onChange={handleChange} name="category">
          <option value="sneakers">Sneakers</option>
          <option value="tshirts">T-shirts</option>
          <option value="jeans">Jeans</option>
        </select>
        <p>Tags:</p>
        <textarea
          ref={tagRef}
          placeholder="Seperate tags with commas..."
        ></textarea>
        <button onClick={handleTags} type="button">
          Add Tags
        </button>
        <div className="tags">
          {state.tags.map((tag) => (
            <small
              onClick={() => dispatch({ type: "REMOVE_TAG", payload: tag })}
              key={tag}
            >
              {tag}
            </small>
          ))}
        </div>
        <div className="quantity">
          <button onClick={() => dispatch({ type: "DECREASE" })} type="button">
            -
          </button>
          <span>Quantity ({state.quantity})</span>
          <button onClick={() => dispatch({ type: "INCREASE" })} type="button">
            +
          </button>
        </div>
      </form>
    </div>
  );
};

export default Form;



form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  text-align: center;
  margin-top: 5px;
}
button {
  cursor: pointer;
}
.tags {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
small {
  border: 1px solid gray;
  border-radius: 5px;
  padding: 1px 10px;
  cursor: pointer;
}
.quantity{
  margin-top: 10px;
  display: flex;
  gap: 10px;
}



```

</details>

<details>
      <summary>
        FormReducer 
     </summary>

```javascript
export const INITIAL_STATE = {
  title: "",
  desc: "",
  price: 0,
  category: "",
  tags: [],
  images: {
    sm: "",
    md: "",
    lg: "",
  },
  quantity: 0,
};

export const formReducer = (state, action) => {
  switch (action.type) {
    case "CHANGE_INPUT":
      return {
        ...state,
        [action.payload.name]: action.payload.value,
      };
    case "ADD_TAG":
      return {
        ...state,
        tags: [...state.tags, action.payload],
      };
    case "REMOVE_TAG":
      return {
        ...state,
        tags: state.tags.filter((tag) => tag !== action.payload),
      };
    case "INCREASE":
      return {
        ...state,
        quantity: state.quantity + 1,
      };
    case "DECREASE":
      return { ...state, quantity: state.quantity - 1 };
    default:
      return state;
  }
};
```

</details>
<details>
      <summary>
      Post reducer 
     </summary>

```javascript
import { useReducer, useState } from "react";
import { ACTION_TYPES } from "./postActionTypes";
import { INITIAL_STATE, postReducer } from "./postReducer";

const Post = () => {
  // USING USESTATE

  // const [loading, setLoading] = useState(false);
  // const [error, setError] = useState(false);
  // const [post, setPost] = useState({});

  // const handleFetch = () => {
  //   setLoading(true);
  //   setError(false);
  //   fetch("https://jsonplaceholder.typicode.com/posts/1")
  //     .then((res) => res.json())
  //     .then((data) => {
  //       setLoading(false);
  //       setPost(data);
  //     })
  //     .catch((err) => {
  //       setLoading(false);
  //       setError(true);
  //     });
  // };

  //USING USEREDUCER

  const [state, dispatch] = useReducer(postReducer, INITIAL_STATE);

  const handleFetch = () => {
    dispatch({ type: ACTION_TYPES.FETCH_START });
    fetch("")
      .then((res) => {
        return res.json();
      })
      .then((data) => {
        dispatch({ type: ACTION_TYPES.FETCH_SUCCESS, payload: data });
      })
      .catch((err) => {
        dispatch({ type: ACTION_TYPES.FETCH_ERROR });
      });
  };

  return (
    //USING USESTATE

    // <div>
    //   <button onClick={handleFetch}>
    //     {loading ? "Wait..." : "Fetch the post"}
    //   </button>
    //   <p>{post?.title}</p>
    //   <span>{error && "Something went wrong!"}</span>
    // </div>

    //USING USEREDUCER

    <div>
      <button onClick={handleFetch}>
        {state.loading ? "Wait..." : "Fetch the post"}
      </button>
      <p>{state.post?.title}</p>
      <span>{state.error && "Something went wrong!"}</span>
    </div>
  );
};

export default Post;




div {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
  text-align: center;
}
button {
  margin-top: 10px;
  cursor: pointer;
}
span {
  color: red;
}

```

</details>
<details>
      <summary>
        Post reduCers 
     </summary>

```javascript
import { ACTION_TYPES } from "./postActionTypes";

export const INITIAL_STATE = {
  loading: false,
  post: {},
  error: false,
};

export const postReducer = (state, action) => {
  switch (action.type) {
    case ACTION_TYPES.FETCH_START:
      return {
        loading: true,
        error: false,
        post: {},
      };
    case ACTION_TYPES.FETCH_SUCCESS:
      return {
        ...state,
        loading: false,
        post: action.payload,
      };
    case ACTION_TYPES.FETCH_ERROR:
      return {
        error: true,
        loading: false,
        post: {},
      };
    default:
      return state;
  }
};

export const ACTION_TYPES = {
  FETCH_START: "FETCH_START",
  FETCH_SUCCESS: "FETCH_SUCCESS",
  FETCH_ERROR: "FETCH_ERROR",
};
```

</details>

</br>
</br>
</br>
<details>
      <summary>
       todo app
     </summary>

```javascript

Todo.js;
todo.module.css;

import React from "react";

import style from "./todo.module.css";

const Todo = (props) => {
  const { title, desc } = props.todo;
  const { id } = props;
  const handleClick = (id) => {
    props.onRemoveTodo(id);
  };
  return (
    <article className={style.todo}>
      <div>
        <h3>{title}</h3>
        <p>{desc}</p>
      </div>
      <div>
        <button
          className={style.btn}
          onClick={() => {
            handleClick(id);
          }}
        >
          <i className="fa fa-trash fa-2x"></i>
        </button>
      </div>
    </article>
  );
};

export default Todo;



Todos.js;
todos.module.css;


import React from "react";

import Todo from "./Todo";
import style from "./todos.module.css";

const Todos = (props) => {
  return (
    <section className={style.todos}>
      {props.todos.map((todo, index) => {
        return (
          <Todo
            todo={todo.todo}
            key={todo.id}
            id={todo.id}
            onRemoveTodo={props.onRemoveTodo}
          />
        );
      })}
    </section>
  );
};

export default Todos;




Home.js;
home.module.css;

import React, { useState } from "react";

import { v4 as uuidv4 } from "uuid";

import Todos from "./Todos";
import style from "./home.module.css";
import NewTodo from "./NewTodo";

const Home = () => {
  const [todos, setTodos] = useState([]);

  const handleAddTodo = (todo) => {
    setTodos((prevTodos) => {
      return [...prevTodos, { id: uuidv4(), todo }];
    });
  };

  const handleRemoveTodo = (id) => {
    setTodos((prevTodos) => {
      const filteredTodos = prevTodos.filter((todo) => todo.id !== id);
      return filteredTodos;
    });
  };

  return (
    <div className={style.container}>
      <h1 style={{ color: "white" }}>Todo App</h1>
      <NewTodo onAddTodo={handleAddTodo} />
      {todos && <Todos todos={todos} onRemoveTodo={handleRemoveTodo} />}
      <button
        className={style.btn}
        onClick={() => {
          setTodos([]);
        }}
      >
        Clear All todos
      </button>
    </div>
  );
};

export default Home;



NewTodo.js;
newtodo.module.css;

import React, { useState } from "react";

import style from "./newtodo.module.css";
const NewTodo = (props) => {
  const [todo, setTodo] = useState({ title: "", desc: "" });
  const { title, desc } = todo;

  const handleChange = (event) => {
    const name = event.target.name;
    setTodo((oldTodo) => {
      return { ...oldTodo, [name]: event.target.value };
    });
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    props.onAddTodo(todo);
    setTodo({ title: "", desc: "" });
  };

  return (
    <form className={style.form} onSubmit={handleSubmit}>
      <div className={style["form-field"]}>
        <label htmlFor="title">Title: </label>
        <input
          type="text"
          id="title"
          name="title"
          value={title}
          onChange={handleChange}
        />
      </div>
      <div className={style["form-field"]}>
        <label htmlFor="desc">Description: </label>
        <textarea
          type="text"
          id="desc"
          name="desc"
          value={desc}
          onChange={handleChange}
        />
      </div>
      <button type="submit">Add todo</button>
    </form>
  );
};

export default NewTodo;


```

</details>
<details>
      <summary>
        hello
     </summary>

```javascript
import React from "react";

const Expensive = () => {
  console.log("expensive compenent rendered!");

  let total = 0;
  for (let i = 0; i < 1000000000; i++) {
    total += i;
  }

  return <div>Expensive</div>;
};

export default Expensive;
```

</details>
<details>
      <summary>
        hello
     </summary>

```javascript
import React from "react";

const Expensive = () => {
  console.log("expensive compenent rendered!");

  let total = 0;
  for (let i = 0; i < 1000000000; i++) {
    total += i;
  }

  return <div>Expensive</div>;
};

export default Expensive;
```

</details>
<details>
      <summary>
        hello
     </summary>

```javascript
import React from "react";

const Expensive = () => {
  console.log("expensive compenent rendered!");

  let total = 0;
  for (let i = 0; i < 1000000000; i++) {
    total += i;
  }

  return <div>Expensive</div>;
};

export default Expensive;
```

</details>
<details>
      <summary>
        hello
     </summary>

```javascript
import React from "react";

const Expensive = () => {
  console.log("expensive compenent rendered!");

  let total = 0;
  for (let i = 0; i < 1000000000; i++) {
    total += i;
  }

  return <div>Expensive</div>;
};

export default Expensive;
```

</details>
<details>
      <summary>
        hello
     </summary>

```javascript
import React from "react";

const Expensive = () => {
  console.log("expensive compenent rendered!");

  let total = 0;
  for (let i = 0; i < 1000000000; i++) {
    total += i;
  }

  return <div>Expensive</div>;
};

export default Expensive;
```

</details>
<details>
      <summary>
        hello
     </summary>

```javascript
import React from "react";

const Expensive = () => {
  console.log("expensive compenent rendered!");

  let total = 0;
  for (let i = 0; i < 1000000000; i++) {
    total += i;
  }

  return <div>Expensive</div>;
};

export default Expensive;
```

</details>
