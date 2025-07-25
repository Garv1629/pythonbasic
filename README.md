<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Synthora AI Bootcamp - Weekly Slides</title>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;500;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Outfit', sans-serif;
      background: linear-gradient(to right, #0a0f1c, #101e4a);
      overflow: hidden;
      color: #fff;
    }
    .carousel-container {
      position: relative;
      width: 100vw;
      height: 100vh;
      overflow: hidden;
    }
    .carousel {
      display: flex;
      transition: transform 0.8s ease-in-out;
      width: 700vw;
      height: 100%;
    }
    .slide {
      flex: 0 0 100vw;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(145deg, #0a0f1c, #101e4a);
      position: relative;
      padding: 1rem;
    }
    .card {
      background: rgba(0, 255, 247, 0.08);
      backdrop-filter: blur(18px);
      -webkit-backdrop-filter: blur(18px);
      border-radius: 24px;
      padding: 2rem;
      max-width: 800px;
      width: 100%;
      text-align: left;
      box-shadow: 0 0 40px rgba(0, 255, 255, 0.3);
      animation: fadeInUp 0.8s ease;
    }
    @keyframes fadeInUp {
      0% {
        opacity: 0;
        transform: translateY(50px);
      }
      100% {
        opacity: 1;
        transform: translateY(0);
      }
    }
    h1 {
      font-size: 2rem;
      color: #00fff7;
      margin-bottom: 1rem;
      text-shadow: 0 0 14px rgba(0,255,255,0.4);
    }
    h2 {
      font-size: 1.2rem;
      margin-top: 1rem;
      color: #86f1f1;
    }
    p {
      font-size: 1rem;
      line-height: 1.6;
      color: #e0f7ff;
      margin-bottom: 1rem;
    }
    ul {
      margin-left: 1.2rem;
    }
    li {
      margin: 0.3rem 0;
    }
    .social {
      margin-top: 1.5rem;
      display: flex;
      flex-wrap: wrap;
    }
    .social a {
      color: #00fff7;
      margin-right: 12px;
      text-decoration: none;
      font-weight: 500;
      font-size: 0.9rem;
    }
    .nav-arrows {
      position: absolute;
      top: 50%;
      width: 100%;
      display: flex;
      justify-content: space-between;
      transform: translateY(-50%);
      padding: 0 1rem;
      z-index: 10;
    }
    .arrow {
      font-size: 2rem;
      color: #00fff7;
      cursor: pointer;
      transition: 0.2s ease;
    }
    .arrow:hover {
      transform: scale(1.2);
    }

    @media (max-width: 768px) {
      .card {
        padding: 1.5rem;
        font-size: 0.95rem;
      }
      h1 {
        font-size: 1.6rem;
      }
      h2 {
        font-size: 1rem;
      }
      p, li {
        font-size: 0.95rem;
      }
      .arrow {
        font-size: 1.5rem;
      }
    }
  </style>
</head>
<body>
  <div class="carousel-container">
    <div class="carousel" id="carousel">
      <!-- Slides Injected Here -->
    </div>
    <div class="nav-arrows">
      <div class="arrow" onclick="prevSlide()">&#10094;</div>
      <div class="arrow" onclick="nextSlide()">&#10095;</div>
    </div>
  </div>
  <script>
    const carousel = document.getElementById('carousel');
    let currentSlide = 0;
    const totalSlides = 7;

    const slideContent = [
      {
        title: "Week 1: Python Programming",
        topics: ["Python syntax, variables, operators", "Data types, conditionals, loops", "Functions, input/output, error handling"],
        handsOn: "Mini calculator, ATM simulation, simple games",
        outcome: "Strong programming logic + Python foundations"
      },
      {
        title: "Week 2: NumPy & Pandas",
        topics: ["NumPy arrays, matrix ops, slicing, broadcasting", "Pandas Series, DataFrames, filtering, grouping", "Reading/writing CSV/Excel files"],
        handsOn: "Data cleaning, movie dataset analysis, basic data wrangling",
        outcome: "Mastery in data manipulation with Python"
      },
      {
        title: "Week 3: Data Visualization",
        topics: ["Matplotlib and Seaborn basics", "Bar, pie, histogram, line, scatter, heatmaps", "Custom styling, labels, legends"],
        handsOn: "Create dashboard-style EDA visualizations",
        outcome: "Skills to communicate data insights visually"
      },
      {
        title: "Week 4: Supervised Machine Learning",
        topics: ["Regression (Linear, Ridge, Lasso)", "Classification (KNN, Decision Tree, SVM)", "Model evaluation metrics"],
        handsOn: "Train/test ML models on real datasets",
        outcome: "Ability to build, train, and evaluate ML models"
      },
      {
        title: "Week 5: Clustering & PCA",
        topics: ["KMeans clustering, DBSCAN", "PCA, t-SNE, feature scaling", "Elbow method, dimensionality reduction"],
        handsOn: "Cluster customer segments, visualize reduced features",
        outcome: "Master unsupervised learning + visual exploration"
      },
      {
        title: "Week 6: Deep Learning Intro",
        topics: ["ANNs, layers, activation functions", "Backpropagation, epochs, batch size", "TensorFlow, Keras"],
        handsOn: "Train neural networks on image/text datasets",
        outcome: "Understand and apply basics of neural networks"
      },
      {
        title: "Week 7: Capstone + Deployment",
        topics: ["Complete ML pipeline: clean → model → deploy", "Streamlit app development", "Deploy on HuggingFace, GitHub, Render"],
        handsOn: "Build full ML app + host it live + shareable link",
        outcome: "Real-world project + resume-ready + certificate awarded"
      }
    ];

    function renderSlides() {
      slideContent.forEach(week => {
        const slide = document.createElement("div");
        slide.className = "slide";
        slide.innerHTML = `
          <div class="card">
            <h1>${week.title}</h1>
            <h2>📌 Topics Covered:</h2>
            <ul>${week.topics.map(topic => `<li>${topic}</li>`).join('')}</ul>
            <h2>🧪 Hands-On:</h2>
            <p>${week.handsOn}</p>
            <h2>🎯 Outcome:</h2>
            <p>${week.outcome}</p>
            <div class="social">
              <a href="https://instagram.com/synthoradigital" target="_blank">Instagram</a>
              <a href="https://linkedin.com/in/synthoradigital" target="_blank">LinkedIn</a>
              <a href="https://youtube.com/@synthoradigital" target="_blank">YouTube</a>
            </div>
          </div>
        `;
        carousel.appendChild(slide);
      });
    }

    function goToSlide(index) {
      currentSlide = index;
      carousel.style.transform = `translateX(-${index * 100}vw)`;
    }

    function nextSlide() {
      currentSlide = (currentSlide + 1) % totalSlides;
      goToSlide(currentSlide);
    }

    function prevSlide() {
      currentSlide = (currentSlide - 1 + totalSlides) % totalSlides;
      goToSlide(currentSlide);
    }

    renderSlides();
    goToSlide(0);
  </script>
</body>
</html>
