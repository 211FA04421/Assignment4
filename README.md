# Assignment4
#index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Food Gallery</title>
    <link rel="stylesheet" href="index.css"/>
</head>
<header id="header">
    <h1>Food Gallery</h1>
</header>
<body>
    <section id="sec-1_sec-3">
        <button id="btn-1">Explore Recipes</button>
    </section>
    <div id="main" class="aa">
    </div>
</body>
<footer id="footer">
    <p id="foo">© 2024 Food Gallery | All Rights Reserved</p>
</footer>
<script src="index.js"></script>
</html>

#index.css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background-color: #f8f9fa;
    color: #333;
}

#header {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
    background-color: #28a745;
    color: white;
}

h1 {
    font-size: 2.5em;
    text-transform: uppercase;
    letter-spacing: 2px;
}

#sec-1_sec-3 {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 20px 0;
}

#btn-1 {
    font-size: large;
    color: white;
    background-color: #343a40;
    border-radius: 12px;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
}

#btn-1:hover {
    background-color: #495057;
}

.div-1 {
    display: flex;
    flex-direction: column;
    background-color: #ffffff;
    padding: 15px;
    border-radius: 12px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin-bottom: 20px;
    width: 300px;
    text-align: center;
}

.title {
    font-size: 1.2em;
    margin-bottom: 10px;
    color: #28a745;
}

.img-0 {
    width: 100%;
    height: auto;
    border-radius: 12px;
    margin-bottom: 10px;
}

.btn-2 {
    font-size: medium;
    background-color: #28a745;
    color: white;
    padding: 8px 16px;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    text-transform: uppercase;
}

.btn-2:hover {
    background-color: #218838;
}

.a {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

#main {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    gap: 20px;
    padding: 20px;
}

#footer {
    text-align: center;
    padding: 20px;
    background-color: #const btn = document.getElementById("btn-1");
btn.addEventListener("click", async () => {
    find()
        .then((data) => {
            let i = 10;
            const parent = document.getElementById("main");
            const child = document.getElementById("div1");
            if (parent.contains(child)) {
                for (let n = 1; n <= 10; n++) {
                    parent.removeChild(document.getElementById(`div${n}`));
                }
            }

            while (i-- > 0) {
                let new1 = document.createElement('div');
                new1.className = 'div-1';
                new1.setAttribute("id", `div${i + 1}`);

                let new2 = document.createElement('section');
                new2.className = 'sec-1';
                new2.setAttribute("id", `sec${i}`);

                let new3 = document.createElement('section');
                new3.className = 'sec-1_sec-1';
                new3.setAttribute("id", `sec-1_sec-1${i}`);

                let new4 = document.createElement('section');
                new4.className = 'add';
                new4.setAttribute("id", `add${i}`);

                let new5 = document.createElement('img');
                new5.setAttribute("id", `img${i}`);
                new5.className = 'img-0';
                new5.src = data[i].img;

                let new6 = document.createElement('a');
                new6.href = data[i].link;
                new6.textContent = "Watch Recipe";
                new6.className = 'a';
                new6.setAttribute("target", "_blank");

                let new7 = document.createElement('button');
                new7.className = 'btn-2';
                new7.setAttribute("id", `btn${i}`);

                let newBox = document.createElement('h3');
                newBox.className = 'title';
                newBox.textContent = data[i].name;

                document.getElementById('main').appendChild(new1);
                new1.appendChild(new2);
                new1.appendChild(new7);
                new2.appendChild(new3);
                new3.appendChild(new4);
                new4.appendChild(newBox);
                new4.appendChild(new5);
                new7.appendChild(new6);
            }
        })
        .catch(err => {
            let title = document.getElementsByClassName("title")[0];
            title.textContent = err;
        });
});

function find() {
    return new Promise((resolve, reject) => {
        let items = [];
        setTimeout(async () => {
            let n = 9;
            while (n-- > 0) {
                let url = `https://www.themealdb.com/api/json/v1/1/random.php`;
                let data = await fetch(url);
                let { meals } = await data.json();
                let item = {
                    name: meals[0].strMeal,
                    img: meals[0].strMealThumb,
                    link: meals[0].strYoutube
                }
                items.push(item);
            }
            let url = `https://www.themealdb.com/api/json/v1/1/random.php`;
            let data = await fetch(url);
            let { meals } = await data.json();
            let item = {
                name: meals[0].strMeal,
                img: meals[0].strMealThumb,
                link: meals[0].strYoutube
            }
            items.push(item);
            console.log(items);
            if (data.ok) {
                resolve(items);
            } else {
                reject(`data.error`);
            }
        }, 1000);
    });
}
343a40;
    color: white;
    margin-top: 50px;
}

#foo {
    font-size: 1.1em;
}

#index.js
