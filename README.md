<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    #gifContainer img {
      width: 25%;
    }
  </style>
</head>

<body>
  <div>week 20</h4>

  <div id="gifContainer"></div>
  <div id="mainContent"></div>

  <script>

    let myRequest = new XMLHttpRequest();

    const GIPHY_API_KEY = 'WOVQUcSFOnSD2qeS3UyiqkiaBiJlUhLX';
    const category = 'joey';

    myRequest.onreadystatechange = function (event) {

      if (myRequest.status === 200) {
        let parsedGifs = JSON.parse(myRequest.response)
        console.log(parsedGifs);

        for (let i = 0; i < 16; i++) {
          let image = document.createElement('img');
          image.setAttribute('src', parsedGifs.data[i].images.original.url);
          gifContainer.appendChild(image);
        }
      }
    };

    myRequest.onload = () => {
      console.log("onload", myRequest.status);
    };

    myRequest.open('GET', 'http://api.giphy.com/v1/gifs/search?api_key=' + GIPHY_API_KEY + '&q=' + category);
    myRequest.setRequestHeader('Accept', 'application/json');
    myRequest.setRequestHeader('Content-Type', 'application/json');
    myRequest.send(null);

  </script>
</body>

</html>
