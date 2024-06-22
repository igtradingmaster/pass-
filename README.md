
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Text Editor</title>
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .no-copy {
    -webkit-user-select: none;  /* Safari */
    -moz-user-select: none;     /* Firefox */
    -ms-user-select: none;      /* Internet Explorer/Edge */
    user-select: none;          /* Standard syntax */
}
        body {
            background-color: #00060b;
            font-family: 'Arial', sans-serif;
        }

        .container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
        }

        h2 {
            font-weight: bold;
            color: #343a40;
            text-align: center;
            margin-bottom: 30px;
        }

        .form-group label {
            font-weight: bold;
            color: #495057;
        }

        .form-control-file {
            border: 1px solid #ced4da;
            border-radius: 5px;
            padding: 10px;
        }

        #file-content {
            background-color: #e9ecef;
            border: 1px solid #ced4da;
            border-radius: 5px;
            padding: 20px;
            margin-top: 15px;
            height: 200px;
            overflow-y: auto;
            white-space: pre-wrap;
            word-wrap: break-word;
        }

        #copy-button {
            display: block;
            width: 100%;
            margin-top: 20px;
            padding: 10px;
            font-size: 16px;
            font-weight: bold;
            color: #ffffff;
            background-color: #007bff;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }

        #copy-button:hover {
            background-color: #0056b3;
        }
        li{
            color: red;
            background-color: #ced4da;
        }
        #exitLogo {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 50px; /* Fixed width */
  height: 50px; /* Fixed height */
  display: flex;
  justify-content: center;
  align-items: center;
}

#exitLogo img {
  width: 100%;
  height: 100%;
  object-fit: contain; /* Maintain aspect ratio */
}
h1{
display:none;
}
    </style>
</head>
<body>

<div class="container mt-5">
    <div class="row">
        <div class="col-md-12">
            <div class="no-copy">
                <a href="https://igtradingmaster.github.io/Home/" id="exitLogo">
                    <img src="https://t3.ftcdn.net/jpg/04/51/52/52/360_F_451525222_IKqxMEeAVBS6Pj5JpJU0MxnQAtasHZPe.jpg" alt="Exit Logo">
                  </a>
              </div>
            <h2 class="mb-4">Txt Reader</h2>
            <center><li>Allow Only TXT Files</li></center>
            <div class="form-group">
                <label for="file-input">Upload a file:</label>
                <input type="file" class="form-control-file" id="file-input" accept=".txt">
            </div>
            <div class="form-group">
                <label for="file-content">File Content:</label>
                <div id="file-content" class="box"></div>
            </div>
            <button class="btn btn-primary" id="copy-button">Copy Text</button>
        </div>
    </div>
</div>
</div>

<script>
    document.getElementById('file-input').addEventListener('change', function(event) {
        const file = event.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = function(e) {
                document.getElementById('file-content').textContent = e.target.result;
            };
            reader.readAsText(file);
        }
    });

    document.getElementById('copy-button').addEventListener('click', function() {
        const content = document.getElementById('file-content').textContent;
        navigator.clipboard.writeText(content).then(() => {
            alert('Text copied to clipboard');
        }).catch(err => {
            alert('Failed to copy text: ', err);
        });
    });
</script>

</body>
