<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DANI CLOTHES - Men's Fashion</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.css"/>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick-theme.css"/>
    <style>
        /* Global Styles */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Montserrat', sans-serif; color: #333; background: #f9f9f9; line-height: 1.6; }
        h1, h2, h3 { font-family: 'Playfair Display', serif; }
        a { text-decoration: none; color: inherit; }
        button { font-family: inherit; cursor: pointer; transition: all 0.3s ease; }
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }

        /* Dark Mode */
        body.dark { background: #222; color: #ddd; }
        body.dark .hero, body.dark .categories, body.dark .products, body.dark .about, body.dark .newsletter { background: #333; color: #ddd; }
        body.dark .btn { background: #555; color: #ddd; }

        /* Header */
        header { position: sticky; top: 0; background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(10px); z-index: 100; box-shadow: 0 2px 5px rgba(0,0,0,0.1); transition: all 0.3s; }
        header.dark { background: rgba(34,34,34,0.95); }
        .nav { display: flex; justify-content: space-between; align-items: center; padding: 20px; }
        .logo { font-size: 24px; font-weight: 700; color: #333; }
        .menu { display: flex; list-style: none; gap: 30px; }
        .menu li a { font-weight: 500; transition: color 0.3s; }
        .menu li a:hover { color: #d4af37; }
        .icons { display: flex; gap: 15px; font-size: 20px; }
        .icons a:hover { color: #d4af37; }

        /* Hero */
        .hero { background: url('https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80') center/cover no-repeat; height: 80vh; display: flex; align-items: center; justify-content: center; text-align: center; color: white; position: relative; }
        .hero::before { content: ''; position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.3); }
        .hero-content { position: relative; z-index: 1; }
        .hero h1 { font-size: 48px; margin-bottom: 10px; }
        .hero p { font-size: 18px; margin-bottom: 20px; }
        .btn { background: #d4af37; color: white; padding: 12px 24px; border: none; border-radius: 25px; font-weight: 500; }
        .btn:hover { background: #b8952a; }

        /* Sign-Up Modal */
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); z-index: 200; }
        .modal-content { background: white; margin: 15% auto; padding: 20px; width: 90%; max-width: 400px; border-radius: 10px; box-shadow: 0 5px 15px rgba(0,0,0,0.3); text-align: center; }
        .modal-content.dark { background: #333; color: #ddd; }
        .modal-content input { width: 100%; padding: 10px; margin: 10px 0; border: 1px solid #ccc; border-radius: 5px; }
        .modal-content button { width: 100%; margin: 10px 0; }

        /* Sections */
        section { padding: 60px 0; }
        .categories { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; }
        .category-card { background: white; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 10px rgba(0,0,0,0.1); transition: transform 0.3s; }
        .category-card:hover { transform: translateY(-5px); }
        .category-card img { width: 100%; height: 200px; object-fit: cover; }
        .category-card h3 { padding: 15px; text-align: center; }

        .products { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; }
        .product-card { background: white; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 10px rgba(0,0,0,0.1); transition: transform 0.3s; position: relative; }
        .product-card:hover { transform: scale(1.05); }
        .product-card img { width: 100%; height: 250px; object-fit: cover; }
        .product-card .overlay { position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.5); display: flex; align-items: center; justify-content: center; opacity: 0; transition: opacity 0.3s; }
        .product-card:hover .overlay { opacity: 1; }
        .product-card .overlay button { background: #d4af37; color: white; padding: 10px 20px; border: none; border-radius: 25px; }

        .new-arrivals .slick-slide { margin: 0 10px; }
        .new-arrivals img { width: 100%; height: 200px; object-fit: cover; border-radius: 10px; }

        .about { text-align: center; }
        .about img { width: 100%; max-width: 500px; margin: 20px 0; border-radius: 10px; }

        .newsletter { background: #e8e8e8; text-align: center; }
        .newsletter.dark { background: #444; }

        /* Footer */
        footer { background: #222; color: white; padding: 40px 0; }
        .footer-content { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; }
        .footer-content h4 { margin-bottom: 10px; }
        .social-icons { display: flex; gap: 15px; font-size: 24px; }
        .payment-icons { display: flex; gap: 10px; margin-top: 10px; }

        /* Animations */
        .fade-in { opacity: 0; animation: fadeIn 1s ease-in-out forwards; }
        @keyframes fadeIn { to { opacity: 1; } }

        /* Responsive */
        @media (max-width: 768px) { .nav { flex-direction: column; } .menu { margin: 10px 0; } .hero h1 { font-size: 36px; } }
    </style>
</head>
<body>
    <!-- Dark Mode Toggle -->
    <button id="dark-mode-toggle" style="position: fixed; top: 10px; right: 10px; z-index: 300; background: #d4af37; color: white; border: none; padding: 10px; border-radius: 50%;">🌙</button>

    <!-- Header -->
    <header>
        <nav class="nav container">
            <div class="logo">DANI CLOTHES</div>
            <ul class="menu">
                <li><a href="#home">Home</a></li>
                <li><a href="#shop">Shop</a></li>
                <li><a href="#new-arrivals">New Arrivals</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="icons">
                <a href="#">🔍</a>
                <a href="#">🛒</a>
                <a href="#">👤</a>
            </div>
        </nav>
    </header>

    <!-- Hero -->
    <section id="home" class="hero">
        <div class="hero-content fade-in">
            <h1>DANI CLOTHES</h1>
            <p>CLASS MEETS COMFORT.<br>Shop the latest in men's aesthetic wear.</p>
            <button class="btn" onclick="openModal()">Shop Now</button>
        </div>
    </section>

    <!-- Sign-Up Modal -->
    <div id="signup-modal" class="modal">
        <div class="modal-content">
            <h2>Sign Up / Sign In</h2>
            <button class="btn">Continue with Google</button>
            <input type="email" placeholder="Email">
            <input type="password" placeholder="Password">
            <button class="btn">Sign Up</button>
            <button class="btn" onclick="closeModal()">Close</button>
        </div>
    </div>

    <!-- Featured Categories -->
    <section class="categories container fade-in">
        <h2 style="text-align: center; margin-bottom: 40px;">Featured Categories</h2>
        <div class="category-card">
            <img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Casual Wear">
            <h3>Casual Wear</h3>
            <button class="btn">Explore</button>
        </div>
        <div class="category-card">
            <img src="https://images.unsplash.com/photo-1594938298603-c8148c4dae35?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Formal Wear">
            <h3>Formal Wear</h3>
            <button class="btn">Explore</button>
        </div>
        <div class="category-card">
            <img src="https://images.unsplash.com/photo-1551107696-a4b0c5a0d9a2?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Streetwear">
            <h3>Streetwear</h3>
            <button class="btn">Explore</button>
        </div>
        <div class="category-card">
            <img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Winter Collection">
            <h3>Winter Collection</h3>
            <button class="btn">Explore</button>
        </div>
    </section>

    <!-- Product Showcase -->
    <section class="products container fade-in">
        <h2 style="text-align: center; margin-bottom: 40px;">Product Showcase</h2>
        <div class="product-card">
            <img src="https://images.unsplash.com/photo-1596755094514-f87e34085b2c?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Linen Casual Shirt">
            <div class="overlay"><button class="btn">Quick View</button></div>
            <h3>Linen Casual Shirt</h3>
            <p>PKR 2,499</p>
            <button class="btn">Add to Cart</button>
        </div>
        <div class="product-card">
            <img src="https://images.unsplash.com/photo-1542272604-787c3835535d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Slim Fit Trousers">
            <div class="overlay"><button class="btn">Quick View</button></div>
            <h3>Slim Fit Trousers</h3>
            <p>PKR 3,199</p>
            <button class="btn">Add to Cart</button>
        </div>
        <div class="product-card">
            <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Classic Black Blazer">
            <div class="overlay"><button class="btn">Quick View</button></div>
            <h3>Classic Black Blazer</h3>
            <p>PKR 8,999</p>
            <button class="btn">Add to Cart</button>
        </div>
        <div class="product-card">
            <img src="https://images.unsplash.com/photo-1529139574466-a303027c1d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Streetwear Oversized Tee">
            <div class="overlay"><button class="btn">Quick View</button></div>
            <h3>Streetwear Oversized Tee</h3>
            <p>PKR 1,999</p>
            <button class="btn">Add to Cart</button>
        </div>
    </section>

    <!-- New Arrivals -->
    <section id="new-arrivals" class="new-arrivals container fade-in">
        <h2 style="text-align: center; margin-bottom: 40px;">New Arrivals</h2>
        <div class="slider">
            <div><img src="https://images.unsplash.com/photo-1591047139829-d91aecb6caea?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="New Arrival 1"></div>
            <div><img src="https://images.unsplash.com/photo-1553062407-98eeb64c6a62?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="New Arrival 2"></div>
            <div><img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="New Arrival 3"></div>
            <div><img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="New Arrival 4"></div>
            <div><img src="https://images.unsplash.com/photo-1594938298603-c8148c4dae35?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="New Arrival 5"></div>
        </div>
    </section>

    <!-- About -->
    <section id="about" class="about container fade-in">
        <h2>About DANI CLOTHES</h2>
        <p>DANI CLOTHES is a modern brand redefining men’s style with an aesthetic edge. Every piece blends comfort, confidence, and clean design — because good style should feel effortless.</p>
        <img src="https://images.unsplash.com/photo-1506629905607-0b5b1b5b5b5b?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Folded Clothes">
    </section>

    <!-- Newsletter -->
    <section class="newsletter fade-in">
        <div class="container">
            <h2>Join the DANI Circle</h2>
            <p>Get 10% off your first order.</p>
            <input type="email" placeholder="Enter your email" style="padding: 10px; width: 300px; margin: 10px; border: 1px solid #ccc; border-radius: 5px;">
            <button class="btn">Subscribe</button>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content container">
            <div>
                <h4>Quick Links</h4>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Shop</a></li>
                    <li><a href="#">New Arrivals</a></li>
                    <li><a href="#">About</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </div>
            <div>
                <h4>Customer Support</h4>
                <ul>
                    <li><a href="#">FAQ</a></li>
                    <li><a href="#">Returns</a></li>
                    <li><a href="#">Shipping</a></li>
                    <li><a href="#">Size Guide</a></li>
                </ul>
            </div>
            <div>
                <h4>Follow Us</h4>
                <div class="social-icons">
                    <a href="#">📷</a> <!-- Instagram -->
                    <a href="#">📘</a> <!-- Facebook -->
                   # danishkumar.github.io
