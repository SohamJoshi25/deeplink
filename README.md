<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>body{
        background-color:#CCCCCC;
    }
    
    .title{
        font-size:3em;
    }
    
    h1{
        text-align:center;
        padding:1rem;
    }
    
    span{
        display:flex;
        flex-direction: column;
        padding:1rem;
        padding-left:30vw;
        padding-right:30vw;
        font-size:1rem;    
    }
    
    span>*{
    
        padding:1rem;
        margin:1rem;
    }
    
    label{
        font-size:2em;
        text-align:center;
    }
    
    input{
        text-align:center;
        border:1px;
        border-style:solid;
    }
    
    button{
        margin:auto;
        width:20%;
    }
    
    .output{
        padding:2rem;
        margin:auto;
        font-size:2em;
    }
    
    a{
        text-align:center;
        padding:1rem;
    }
    
    #output_android,#output_ios{
        margin:0.5em;
    }
    
    .info{
        padding:2em;
        display:block;
        text-align:left;
    }
    
    ol{
        text-align:center;
    }
    </style>
    <title>DeepLinker</title>
</head>
<body>
    <h1 class="title">Welcome to Deep Linker</h1>
    <hr>
    <br>
    <span>
        <label for="input">Enter LINK</label>
        <input type="link" id="input">
        <button id="submit">Submit</button>
    </span>
    <br>
    <br>
    <hr>
    <div class="output">
        <div id="output_android">
            Android:
        </div>
        <div id="output_ios">
            IOS:
        </div>
    </div>
    <hr>
    <br>
    <br>
    <div class="info">
        <h2>Creates deep links of well known links .</h2>
        <h3>List of API Endpoints : GET methods</h3>
            <p>/health</p>
            <p>/info</p>
            <p>/availablelinks</p>
            <p>/?url=your-url-here</p>
    </div>
    <hr>
    <br>
    <br>
    <script>
        document.getElementById("submit").addEventListener('click',async ()=>{
        const link = document.getElementById('input').value;
        console.log(link);
        const OutputAndroid = document.getElementById('output_android');
        const OutputIos = document.getElementById('output_ios');
    
        fetch(`https://deeplink-0h49.onrender.com/?url=${link}`)
            .then((res)=>res.json())
            .then((res)=>{
                console.log(res)
                const android = document.createElement('a');
                android.href = res.deeplink.android;
                android.innerText = res.deeplink.android;
    
                const ios = document.createElement('a');
                ios.href = res.deeplink.android;
                ios.innerText = res.deeplink.ios;
    
                OutputAndroid.appendChild(android);
                OutputIos.appendChild(ios);
    
            }).catch((e)=>{
                window.alert(`URL Not Recognised or Some error occured | ${e}`);
            })
            .catch((e)=>{
                window.alert(e);
            })
    })
    </script>
</body>
</html>
