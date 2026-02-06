<template>
    <header class="header">
        <div class="logo">
            <span>🟦</span>
            <h1>GridNews</h1>
        </div>

        <div class="search">
            <input
                type="text"
                placeholder="Pesquisar notícias..."
                @input="$emit('update:searchQuery', $event.target.value)"
            />
            <button>
                🔍
            </button>
        </div>

        <nav class="nav">
            <a href="#">Home</a>
            <a href="#">Notícias</a>
            <a href="#">Tecnologia</a>
        </nav>

        <button class="cta">Assinar</button>
    </header>
</template>

<script setup>
</script>

<style scoped>
    .header {
        display: grid;
        grid-template-columns: auto 1fr auto auto;
        align-items: center;
        gap: 24px;
        padding: 16px 32px;
        background: rgba(255, 255, 255, 0.85);
        backdrop-filter: blur(10px);
        border-bottom: 1px solid rgba(0, 0, 0, 0.05);
        position: sticky;
        top: 0;
        z-index: 100;
    }
    
    /* Logo */
    .logo {
        display: flex;
        align-items: center;
        gap: 10px;
    }
    
    .logo h1 {
        font-size: 1.4rem;
        font-weight: 700;
    }
    
    /* Pesquisa */
    .search {
        justify-self: center;
        display: flex;
        align-items: center;
        background: white;
        border-radius: 999px;
        padding: 6px 10px;
        width: 100%;
        max-width: 420px;
        box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    }
    
    .search input {
        border: none;
        outline: none;
        flex: 1;
        padding: 6px 10px;
        font-size: 0.95rem;
    }
    
    .search button {
        background: none;
        border: none;
        font-size: 1.1rem;
        cursor: pointer;
    }
    
    /* Navegação */
    .nav {
        display: flex;
        gap: 20px;
    }
    
    .nav a {
        text-decoration: none;
        color: #444;
        font-weight: 500;
        position: relative;
    }
    
    .nav a::after {
        content: "";
        position: absolute;
        bottom: -6px;
        left: 0;
        width: 0%;
        height: 2px;
        background: #3b82f6;
        transition: width 0.3s ease;
    }
    
    .nav a:hover::after {
        width: 100%;
    }
    
    /* CTA */
    .cta {
        background: #3b82f6;
        color: white;
        border: none;
        padding: 10px 18px;
        border-radius: 999px;
        font-weight: 600;
        cursor: pointer;
    }

    @media (max-width: 768px) {
        .header {
            grid-template-columns: 1fr;
            gap: 16px;
            padding: 16px;
        }

        .nav {
            justify-content: center;
        }

        .search {
            max-width: 100%;
        }

        .cta {
            justify-self: center;
        }
    }
</style>
