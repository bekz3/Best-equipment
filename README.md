[index.html.txt](https://github.com/user-attachments/files/21958622/index.html.txt)
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IPBE — Оборудование ESMA</title>
<style>
    :root {
        --main-color: #1b3b5f;
        --accent-color: #ff9800;
    }
    body { margin:0; font-family: Arial, sans-serif; line-height: 1.5; }
    header { background: var(--main-color); color: white; padding: 30px; text-align: center; }
    nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
    section { padding: 40px 20px; max-width: 1100px; margin: auto; }
    h2 { text-align: center; color: var(--main-color); }
    .products { display: flex; flex-wrap: wrap; gap: 20px; justify-content: center; }
    .product { border: 1px solid #ccc; padding: 15px; border-radius: 8px; width: 250px; text-align: center; background: white; cursor: pointer; transition: transform .2s; }
    .product:hover { transform: scale(1.03); }
    .product img { width: 100%; height: auto; border-radius: 5px; }
    .cta { text-align: center; background: var(--main-color); color: white; padding: 40px 20px; }
    .cta a { background: var(--accent-color); color: white; padding: 12px 25px; text-decoration: none; border-radius: 5px; font-weight: bold; display: inline-block; }
    footer { background: #333; color: white; text-align: center; padding: 20px; font-size: 0.9em; }
    /* Всплывающее окно */
    .modal { display: none; position: fixed; z-index: 10; left: 0; top: 0; width: 100%; height: 100%; overflow: auto;
             background-color: rgba(0,0,0,0.6); }
    .modal-content { background-color: #fff; margin: 10% auto; padding: 20px; border-radius: 8px; max-width: 500px; position: relative; }
    .close { position: absolute; right: 15px; top: 10px; font-size: 28px; cursor: pointer; }
    .modal img { max-width: 100%; border-radius: 5px; margin-bottom: 10px; }
</style>
</head>
<body>

<header>
    <h1>IPBE.kz — Официальный дилер ESMA</h1>
    <nav>
        <a href="#products">Каталог</a>
        <a href="#contact">Контакты</a>
    </nav>
</header>

<section id="products">
    <h2>Хиты продаж</h2>
    <div class="products">
        <div class="product" data-title="ESMA Модель A" data-img="images/product1.jpg" data-desc="Подробное описание модели A. Характеристики, преимущества, гарантия." data-price="95 000 ₸">
            <img src="images/product1.jpg" alt="ESMA Модель A">
            <h3>ESMA Модель A</h3>
            <p><strong>95 000 ₸</strong></p>
        </div>
        <div class="product" data-title="ESMA Модель B" data-img="images/product2.jpg" data-desc="Подробное описание модели B." data-price="105 000 ₸">
            <img src="images/product2.jpg" alt="ESMA Модель B">
            <h3>ESMA Модель B</h3>
            <p><strong>105 000 ₸</strong></p>
        </div>
        <div class="product" data-title="ESMA Модель C" data-img="images/product3.jpg" data-desc="Подробное описание модели C." data-price="115 000 ₸">
            <img src="images/product3.jpg" alt="ESMA Модель C">
            <h3>ESMA Модель C</h3>
            <p><strong>115 000 ₸</strong></p>
        </div>
        <div class="product" data-title="ESMA Модель D" data-img="images/product4.jpg" data-desc="Подробное описание модели D." data-price="125 000 ₸">
            <img src="images/product4.jpg" alt="ESMA Модель D">
            <h3>ESMA Модель D</h3>
            <p><strong>125 000 ₸</strong></p>
        </div>
        <div class="product" data-title="ESMA Модель E" data-img="images/product5.jpg" data-desc="Подробное описание модели E." data-price="135 000 ₸">
            <img src="images/product5.jpg" alt="ESMA Модель E">
            <h3>ESMA Модель E</h3>
            <p><strong>135 000 ₸</strong></p>
        </div>
    </div>
</section>

<!-- Всплывающее окно -->
<div class="modal" id="productModal">
    <div class="modal-content">
        <span class="close">&times;</span>
        <img id="modalImg" src="" alt="">
        <h3 id="modalTitle"></h3>
        <p id="modalDesc"></p>
        <p><strong id="modalPrice"></strong></p>
        <a id="modalOrder" href="#" target="_blank" style="background: var(--accent-color); color:#fff; padding:10px 20px; border-radius:5px; text-decoration:none;">Заказать</a>
    </div>
</div>

<section id="contact" class="cta">
    <h2>Свяжитесь с нами</h2>
    <p>Закажите оборудование или задайте вопрос</p>
    <a href="https://wa.me/77001234567">Написать в WhatsApp</a>
</section>

<footer>
    &copy; 2025 IPBE.kz — Официальный дилер ESMA
</footer>

<script>
    const products = document.querySelectorAll('.product');
    const modal = document.getElementById('productModal');
    const modalImg = document.getElementById('modalImg');
    const modalTitle = document.getElementById('modalTitle');
    const modalDesc = document.getElementById('modalDesc');
    const modalPrice = document.getElementById('modalPrice');
    const modalOrder = document.getElementById('modalOrder');
    const closeBtn = document.querySelector('.close');

    products.forEach(item => {
        item.addEventListener('click', () => {
            modalImg.src = item.dataset.img;
            modalTitle.textContent = item.dataset.title;
            modalDesc.textContent = item.dataset.desc;
            modalPrice.textContent = item.dataset.price;
            modalOrder.href = `https://wa.me/77001234567?text=Хочу%20заказать%20${encodeURIComponent(item.dataset.title)}`;
            modal.style.display = 'block';
        });
    });

    closeBtn.onclick = () => modal.style.display = 'none';
    window.onclick = (e) => { if(e.target === modal) modal.style.display = 'none'; }
</script>

</body>
</html>
