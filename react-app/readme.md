# React app

## With a react project and a docker file

Let's create an image with nodejs and react  
```docker build -t my-react-app .```

Now we can run the image  
```docker run --rm --name react-container -p 3000:3000 my-react-app```
 