## Routing in Next js.

In a [previous blog post](https://movi.hashnode.dev/a-guide-to-react-router-ckjs8gxdt0osn8ls16m2qdh5b), I wrote about how to achieve dynamic pages on a single app using React Router.  I recently started learning more about Server Side Rendering (SSR) for React and learned how to create a project using Next.js, and I found an even cooler way to achieve dynamic routing for your pages.
In this article, I will show you how routing can be achieved in Next.js.


## What is Next js.
Next js is the most powerful and featured React framework that allows you to build Server-Side Rendering (SSR) and static react applications. It comes with an inbuilt configuration, so you don't need to do that manually 
### Routing:
 Using Next js, routing is a lot easier. Generally, any file that has the extensions *.js, .jsx, .ts, or .tsx * within the *pages* folder of the root directory automatically becomes a route and can be accessed by using the "/" followed by the page name. 
*Eg.*


```
├── pages
|  ├── index.js
|  ├── contact.js
|  └── my-blog 
|     ├── about.js
|     ├── index.js
``` 
The forward-slash (/) helps you route into any page within the pages folder. In the illustration above, to get into *about page* within *my-blog * is seen as:
```
 http://localhost:3000/my-blog/about
``` 
To get into the *contact.js page* with is directly inside the pages is seen as this.

```
 http://localhost:3000/contact
``` 

### Linking between pages
Next.js uses the **Link** component provided by *next/link*, which allows you to do client-side route transitions between pages just like it is done in a single-page app. The Link component requires the *href* attribute for routing.
E.g

```
import Link from 'next/link'

const Home =() =>{
  return (
    <ul>
      <li>
        <Link href="/">
          <a>Home</a>
        </Link>
      </li>
      <li>
        <Link href="/blog/about">
          <a>About</a>
        </Link>
      </li>
    </ul>
  )
}

export default Home
``` 

### Dynamic routing
In Next.js, you can define dynamic routes based on a dynamic URL that is created in these brackets syntax([param]). This will make the file behave like *“:var”* in react-router. You create a folder and place a file with open and closing brackets within it. This will route all the requests to the internal file you created by substituting the content inside the brackets.

```
├── pages
|  ├── contact.js
|  └── my-blog
|     ├── [id].js
|     └── index.js
``` 
In the above workflow, any request that is made to the *my-blog* folder will automatically display the [id].js file.
E.g

```
const Home=() =>{
  return (
    <ul>
      <li>
        <Link href="/">
          <a>Home</a>
        </Link>
      </li>
      
      <li>
        <Link href="/my-blog/[id]" as="/my-blog/id">
          <a>My blog id</a>
        </Link>
      </li>
    </ul>
  )
}
``` 

Thank you for reading this article; this article is written based on my understanding of Next and routing. You can find more content like this on [my blog](https://movi.hashnode.dev/).

### Reference:
- https://movi.hashnode.dev/a-guide-to-react-router-ckjs8gxdt0osn8ls16m2qdh5b
- [what-is-nextjs](https://buttercms.com/blog/what-is-nextjs/)
- https://nextjs.org/learn/basics/create-nextjs-app
- https://www.freecodecamp.org/news/routing-in-nextjs-beginners-guide/
- https://maedahbatool.com/understanding-dynamic-routing-and-api-routes-in-next-js/
- https://www.freecodecamp.org/news/an-introduction-to-next-js-for-everyone-507d2d90ab54/
