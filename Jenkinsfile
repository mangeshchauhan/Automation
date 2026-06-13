pipeline{
    agent any

    environment {
        EC2_HOST = 'ec2-18-214-40-149.compute-1.amazonaws.com'
    }

    stages {
        stage('Checkout') {
           steps {
                echo 'Checking out code...'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to EC2...'
                sh '''
                "ssh -o StrictHostKeyChecking=no ubuntu@${EC2_HOST}
                sudo apt update && sudo apt upgrade -y
                sudo apt install nginx -y
                sudo rm -rf /var/www/html/index.nginx-debian.html
                sudo tee /var/www/html/index.html > /dev/null << 'EOF'
                <!DOCTYPE html>
                <html lang="en">
                <head>
                <meta charset="UTF-8">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>DevOps Pathshala</title>

                <style>
                    *{
            margin:0;
            padding:0;
            box-sizing:border-box;
            font-family: Arial, sans-serif;
        }

        body{
            line-height:1.6;
        }

        header{
            background:#0d6efd;
            color:white;
            padding:20px;
            text-align:center;
        }

        nav{
            background:#222;
            padding:15px;
            text-align:center;
        }

        nav a{
            color:white;
            text-decoration:none;
            margin:0 15px;
            font-weight:bold;
        }

        .hero{
            background:#f4f4f4;
            padding:80px 20px;
            text-align:center;
        }

        .hero h1{
            font-size:45px;
            color:#333;
        }

        .hero p{
            margin-top:15px;
            font-size:20px;
            color:#555;
        }

        .btn{
            display:inline-block;
            margin-top:20px;
            background:#0d6efd;
            color:white;
            padding:12px 25px;
            text-decoration:none;
            border-radius:5px;
        }

        .container{
            width:90%;
            margin:auto;
            padding:40px 0;
        }

        .courses{
            display:flex;
            justify-content:space-around;
            flex-wrap:wrap;
            gap:20px;
        }

        .card{
            width:300px;
            background:white;
            box-shadow:0 0 10px rgba(0,0,0,0.2);
            padding:20px;
            border-radius:10px;
            text-align:center;
        }

        .card h3{
            color:#0d6efd;
        }

        footer{
            background:#222;
            color:white;
            text-align:center;
            padding:20px;
            margin-top:30px;
        }

        @media(max-width:768px){
            .courses{
                flex-direction:column;
                align-items:center;
            }

            .hero h1{
                font-size:32px;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>DevOps Pathshala</h1>
    <p>AWS | DevOps | Terraform | Docker | Kubernetes Training</p>
</header>

<nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#courses">Courses</a>
    <a href="#contact">Contact</a>
</nav>

<section class="hero" id="home">
    <h1>Become a DevOps Engineer</h1>
    <p>Learn AWS, Docker, Kubernetes, Terraform, Jenkins and CI/CD from Industry Experts.</p>
    <a href="#contact" class="btn">Enroll Now</a>
</section>

<section class="container" id="about">
    <h2>About Us</h2>
    <p>
        DevOps Pathshala provides practical training in Cloud Computing,
        AWS, DevOps, Kubernetes, Docker, Terraform, Jenkins and CI/CD.
        Our goal is to make students job-ready through hands-on projects.
    </p>
</section>

<section class="container" id="courses">
    <h2>Our Courses</h2>

    <div class="courses">

        <div class="card">
            <h3>AWS Cloud</h3>
            <p>Learn EC2, VPC, S3, IAM, RDS, Route53 and more.</p>
        </div>

        <div class="card">
            <h3>DevOps</h3>
            <p>Git, Jenkins, Docker, Kubernetes, CI/CD Pipelines.</p>
        </div>

        <div class="card">
            <h3>Terraform</h3>
            <p>Infrastructure as Code on AWS and Azure.</p>
        </div>

    </div>
</section>

<section class="container" id="contact">
    <h2>Contact Us</h2>
    <p><strong>Institute:</strong> DevOps Pathshala</p>
    <p><strong>Location:</strong> Pune</p>
    <p><strong>Phone:</strong> 8999045098</p>
    <p><strong>Email:</strong> info@devopspathshala.com</p>
</section>

<footer>
    <p>© 2026 DevOps Pathshala. All Rights Reserved.</p>
</footer>

</body>
</html>

                "
            }
        }
    }
}