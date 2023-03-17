# Get-started-with-React.js-React-Router-6-


https://www.youtube.com/watch?v=4baq00tHfmA&t=4s


React
https://reactjs.org/



What is React.js ? 
Open source JavaScript
Front end Library 
To create interfaces 
On Web pages  

 
App.js 
import {use state} from ‘react’;
import modal fromScript.js 
const contactMaxBtnel = document.queryselector ( ‘#card-maximilian button’ ) 
let modalEl;
let backdropEl;

Function submitContactDetail (emailInput, event) {
     event.preventDefaut ();
     const enteredEmail = emailInputEl.value;
     // We would typically send the email to some backend server here…
     console.log(enteredEmail);
     modalEl.revome();
     backdropEl.remove;
}

function openContactModal (){
     modalEl = document.createElement (‘dialog’);
     const titleEl = document.createElement (‘h2’);
     titleEl.textContente = ‘Share your email address’;

     modalEl.append (titleEl);

     const contactFormEl = document.createElement (‘from’);

     const  emailInputEl = document.createElement (‘Input’);
     emailInputEl.type = ‘email’;
     emailIputEl.placehoulder = ‘something@example.com’;

     const submitBtnEL = document.createElement (‘button’);
     submitBtnEl.textContent = ‘Submit;
     submitBtnEl.className = ‘btn’;
     
     contactFormEl.addEventListener (
        ‘submit’,
         submitContactDetails.bind (null, emailInputEl)
     );
     contactFormEl.append (emailInputEl);
     contactFormEl.append (SubmitBtnEl);
     modalEl.append (contactFormEl);
     modalEl.open = true;
     modalEl.className = ‘modal’

     backdropEl = document.createElement (‘div’)
     backdropEL.className = ‘backdrop’;
     
     document.body.append (backdropEl);
     document.body.append (modalEL);

}

contactMaxBtnEl.addEventListener (‘click’, openContactModal); 


 ‘/.components / Modal’;
import UserCard from /.components / UserCard

function App () {
     const [showModal, setShowModal] = useState (false);
     
     function toggleModalHendler () {
        setShowModal (( isShowing ) => !isShowing);
}
     return (
        <main>  
           <UserCard onContact = {toggleModalHendler}/>
           {showModal && <Modal onClose={togglerModalHendler} />}
        <main>
);
}


export default App;
App.js
const express = require('express');
const bodyParser = require('body-parser');


const { getStoredPosts, storePosts } = require('./data/posts');


const app = express();


app.use(bodyParser.json());


app.use((req, res, next) => {
  // Attach CORS headers
  // Required when using a detached backend (that runs on a different domain)
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'GET,POST');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');
  next();
});


app.get('/posts', async (req, res) => {
  const storedPosts = await getStoredPosts();
  // await new Promise((resolve, reject) => setTimeout(() => resolve(), 1500));
  res.json({ posts: storedPosts });
});


app.get('/posts/:id', async (req, res) => {
  const storedPosts = await getStoredPosts();
  const post = storedPosts.find((post) => post.id === req.params.id);
  res.json({ post });
});


app.post('/posts', async (req, res) => {
  const existingPosts = await getStoredPosts();
  const postData = req.body;
  const newPost = {
    ...postData,
    id: Math.random().toString(),
  };
  const updatedPosts = [newPost, ...existingPosts];
  await storePosts(updatedPosts);
  res.status(201).json({ message: 'Stored new post.', post: newPost });
});


app.listen(8080);


clear
npm start
>react-crash-course-backend@1.0.0 start
>node app.js 




Modal.js 
import  { userRef } from ‘react’;


function Modal ({on close}) {
     const emailInputEl = userRef();
        function submitHendeler (event) {
        event.preventDefault ();
        const enteredEmail = emailInputEl.current.value;
        console.log (enteredEmail); 
        // We would typically send the email to some backend server here …
        onClose ();
}


return ( 
     <>
          <div className=”backdrop” /> 
              <dialog className = modal open>
              <h2>Share your email address<h2/>
               <from onSubmit = {submitHandler}>
                  <input />
                   type = “email”
                   placeholder=”something@exemple.com”
                  ref={emailInputEl}                  
                 />
                < button className=”btn” />Submit </button>
               </form>
               </dialog>
              </>
);
} 
export default Modal;

Creating New React Project 

React code includes syntax that´s not browser compatible!
Various optimizations should be applied before deploying React Websites 
More complex project setup required 
Projects with tools for improving developer experience & transforming / optimizing the code 

Input and Output

Developer code
function App () {
return <h1>Hello World</h1>
}  

Browser code ( simplified ) 
const el = document .createElement (‘h1’)
el.textContent = ‘Hello World’ 
body.append (el)

React Project
converts your developer-friendly code to browser-compatible code 

https://create-react-app.dev/
https://vitejs.dev/guide/
https://nodejs.org/en/

$
$
$ npx create-react-app
$ npm create vite 
? Project name: > react-crash-course 
? Select a framework:
   Select a variant: > JavaScript 
>     Vanilla 
        Vue
        > React 
        Preact 
        Lit 
        svelte 
> JavaScript 
   TypeScript 

Scaffolding project in /Users/max/development/teaching/react-crash-course …
Done. Now run:

    cd react-crash-course 
    npm install
    npm run dev 

Visual Studio Code 
npm install 
npm start 
npm run dev
> react-crash-course@0.0.0 dev 
Local: http://localhost:5173/

Posts.jsx 
import { Outlet } from ‘react-router-dom’;
   
import PostsList from ‘./components/PostsList’;


function Posts () {
     
 
             
   return (
      <>
           <Outlet />
          <main>
             <PostList 
       
          </main>
     </>
 );
}
  
export default Posts;
export function loader () {
   
}

export async function loader () {
               const response = await  fetch(‘https://localhost:8080 /posts’)
               const resData = await response.json();
               return resData.posts;
} 


main.jsx 
import react from ‘react’;
import reactDOM from ‘react-dom/client’
import {RouterProvider, createBrowserRouter } from ‘react-router-dom;’

import App from ‘./App’
import Posts, { loader as postsLoader } from ‘./ routes/Posts’;
import NewPost, { action as newPostAction} from ‘./routes/NewPost’;
import PostDetails, { loader as postDetailsLoader } from ‘./routes/PostDetails’;
import RootLayout from ‘rootes/RootLayout’;
import ‘./index.css’

const router = createBrowserRouter ([
{
    path: ‘/’, 
    element: <RootLayout />,
    loader: postLoader,
    children: [
{
         path: ‘/’,
         element: <Posts />, 
         loader:postLoader,
         children:[ 
             {path: ‘/create-post’, element < NewPost />, action: newPostAction }],
             {path: ‘/:postId’, element: <PostDetails />, loader: postDetailsLoader }
       ],    
     },
          
   ],
},

  
]);

reactDOM.createRoot(document.getElementById(‘root’)).render (
     <React.StrictMode> 
        <RouterProvider router={router} />
     </ReactStrictMode>
)







Index.css
*  { box-sizing: border-box;
}     

:root {
   min-height: 100vh;
   font-family: Inter, Avenir, Helvetica, Arial, sans-serif;
   font-size: 16px;
   line-height: 24px;
   font-weight: 400;
   background-image:radial-gradiant (ellipse at top left, #7f50e4)
   font-synthesis: none;
   text-rendering: optimizeLegibility;
   -webkit-font-smoothing: antialiased; 
   -moz-osx-font-smoothing:grayscale;
   -webkit-text-size-adjust: 100%;
}

body {
   margin:0;
   color: #e6ddf9;

}


package.json
{
     “name”: “react-crash-course”,
     “private”: true,
     “version”: “0.0.0”,
     “type”: “module”,
      > debug
      “scripts”: {
          “dev”:”vite”,
          “build”: “vita build”,
          “preview”: “vite preview”
},
     “dependencies”: {
          “react”:”^18.2.0”,
          “react-dom”: “^18.2.0”,
},
     “devDependencies”: {
          “@types/react”: “^18.0.17”,
          “@types/react-dom”: “^18.0.6”
          “@vitejs/plugin-react”: “^2.1.0”
          “vite”: “^3.1.0”
}

}


Post.jsx
import { Link } from ‘react-router-dom’;

import classes from ./Post.module.css’;

function Post ({id, author,body}) {
    return (
        <li className={classes.post}>
           <Link to={id}>
           <p classeName={classes.author}>{author}</p>
           <p className={classes.text}>{body}</p>
           </Link>
        </li>
}

export default Post;



npm start
npm run dev
Local: http://localhost:5173/






Post.module.css
.post {
   margin: 1rem 0;
   padding: 1rem;
   background-color: #9c7eee;
   border-radius: 8px;
   box-shadow: 0 1px 4px rgba(0,0,0,0.2);
   animation: animate-in 1s ease-out forwards);
}

.post a{
    text-decoration:none;
}

.author {
   font-size:0.8rem;
   font-weight: bold;
   color:#543280
   margin:0;
   text-transformation: uppercase;
}



.text {
   white-space: pre-wrap;
   font-size: 1.25rem;
   margin: 0.25rem 0 0 0;
   color: #593884
   font-style: italic;

}

@keyframes animate-in {
     from {
        opacity 0;
        transform: translateY(0);
}

}


PostsList.jsx
import {useLoaderData} from ‘react-router-dom’;
import Posts from ‘./Post’;
import classes from ‘./PostsLists.module.css’;

function PostList () {
    const posts = useLoaderData();

      return ( 
        <>

                 { posts.lenght > 0 &&    
                      <ul className={classes.posts}>
                        {posts.map ( (post) => (
                           <Post key={post.id} id={post.id} author={post.author}                   body={post.body}/>)) }      
                   </ul>}


                    )}
                   { posts.lenght === 0 && (
                     <h2>There are no posts yet.</h2>
                     <p>Starting adding some!</p>
                </div>
             )}
        </>

    );
}


export default PostList;

npm install react-router-dom 
npm run dev 
>react-crash-course@0.0.0 dev
>vite



PostsList.module.css
.posts {
     list-style: none;
     max-width: 50rem;
     margin: 1rem auto;
     padding: 1rem 0;
     display: grid;
     gap: 1rem;
     grid-template-columns: repeat (3, 30%);
     justify-content: center;
}

NewPost.jsx

import { Link, Form, redirect } from ‘react-router-dom’;
 
import classes from ‘NewPost.module.css’;
import Modal from ‘../components/Modal’;

function NewPost () {
     

   return (
       < Modal>
      <Form method=’post’ className={classes.form} >
          <p>
               <label htmlFor=”body”>Text</label>
               < textarea id =”body” name=”body” required rows={3} />
          </p>
          <p>
               <label htmlFor=”name”>Your name</label>
               <input 
                   type=”text” id=”name” name=”author” required  />
          </p> 
          <p className={classes.action}>
             <Link to=”..” type “button”>
                Cancel
             </Link>
             <button>Submit</button>
          </p>
      </Form>
   </Modal>
);
}

export default NewPost;

   export async function action ({request}) {
       const formData = await  request.formData();
       const postData = Object.fromEntries (formData); // {body: ‘...’, author: ‘…’} 
       formData.get (‘body’)
       await fetch(‘https://localhost:8080/posts’, {
           method: ‘POST’,
           body: JSON.stringify (postData)
           headers: {
                ‘Content-Type’: ‘application/json’
    },
  });
   return redirect(‘/’);  
}



Modal.jsx
import { useNavigate } from ‘react-router-dom’;
import classes from ‘./Modal.module.css’;

function Modal ({children}) {
  const navigate = useNavigate ();
   function closeHandler () {

     navigate(‘..’);
 } 

    return (
       <>
             <div className={classes.backdrop} onClick={closeHandler} />
             <dialog open classeName={classes.modal}>
        {children}
    </dialog>
    </> 
}

export default Modal; 

clear
npm install react-router-dom 
npm run dev
>react-crash-course@0.0.0 dev
>vite 

cd .. 


NewPost.module.css

.form {
   background-color: #6233b9;
   padding: 1rem;
   width: 20rem;
 }

.form label {
   display: block;
   margin-bottom: 0.05rem;
   color: #eadbfb;
   font-weight: bold;
}

.form input,
.form textarea {
    display:block;
    width: 100%;
}

MainHeader.jsx
import { Link } from ‘react-router-dom’;

import { MdPostAdd,MdMessage } from ‘react-icons/md’;

import classes from ‘./MainHeader.module.css’;

function MainHeader () {
   return (
     <header classeName={classes.header}>
     <h1 classeName={classes.logo}> 
         <MD.Message />
         React Poster 
     </h1>
     <p>
           <Link to=”/create-post” className={classes.button} />
               <MdPostAdd size={18} />
               New Post
          </Link>
      </p>
     </header>
);
}

export default MainHeader;



npm install react-icons
npm run dev


React, Client-Side & Backends

Frontend
React.js
A Single-Page Application ( SPA) 

            HTTP Requests & Responses

Backend
Built with any language & framework
Interacts with server-side, files, database, etc

posts.json
{ “posts” :[]}


clear
npm start

posts.json
{"posts":[{"body":"Testing","author":"Max","id":"0.2747737664042158"}]}


Adding Router 
React App
React Apps are SPAs!
Solution: React Router ( https://reactrouter.com/en/main )
/
Landing Page 
A generic ( marketing ) landing page

/Products Page 
loads & displays a list of products

/products/p-1
Product Details Page 
Loads & display details for the product with the selected id (p-1)

React, Client-Side & Backends 
Frontend
React.js 
A Single-Page Application (SPA) 

Backend
Built with any language & framework 
Interacts with server-side files, database etc 

 
RootLayout.jsx 
import { Outlet } from ‘react-router-dom’;

import MainHeader from ‘..components/MainHeader’;

function RootLayout () {
return 
   <>
       <MainHeader />
       <Outlet />
   </>
  );
}

export default RouteLayout;

MainHeader.module.css

.header {
  /* padding: 2rem 10%; */
  margin: 2rem 10%;
  padding: 1rem;
  text-align: center;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 2px solid #ece1fa;
}

.logo {
  font-size: 2rem;
  display: flex;
  gap: 1.5rem;
  align-items: center;
  color: #ece1fa;
}

.button {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  background-color: #a990fb;
  color: #2a2630;
  border: none;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
  cursor: pointer;
  font-weight: bold;
  text-decoration: none;
  text-decoration: none;
}

.button:hover {
  background-color: #8c6cf7;
}


index.html

<!DOCTYPE html>




<html lang="en">


 <head>


   <meta charset="UTF-8" />


   <link rel="icon" type="image/svg+xml" href="/vite.svg" />


   <meta name="viewport" content="width=device-width, initial-scale=1.0" />


   <title>Vite + React</title>


 </head>


 <body>


   <div id="root"></div>


   <script type="module" src="/src/main.jsx"></script>


 </body>


</html>


RouteLayout.jsx
import { Outlet } from ‘react-router-dom’;

import MainHeader from ‘../components/MainHeader’;

function RootLayout () {
    return <>
       <MainHeader />
       <Outlet />
      
          </>
);
}

export default RootLayout;

PostDetails.jsx
import { useLoaderData, Link } from 'react-router-dom';

import Modal from '../components/Modal';
import classes from './PostDetails.module.css';

function PostDetails() {
  const post = useLoaderData();

  if (!post) {
    return (
      <Modal>
        <main className={classes.details}>
          <h1>Could not find post</h1>
          <p>Unfortunately, the requested post could not be found.</p>
          <p>
            <Link to=".." className={classes.btn}>
              Okay
            </Link>
          </p>
        </main>
      </Modal>
    );
  }
  return (
    <Modal>
      <main className={classes.details}>
        <p className={classes.author}>{post.author}</p>
        <p className={classes.text}>{post.body}</p>
      </main>
    </Modal>
  );
}

export default PostDetails;

export async function loader({params}) {
     const response = await fetch('http://localhost:8080/posts/' + params.postId);
     const resData = await response.json();
  return resData.post;
}
