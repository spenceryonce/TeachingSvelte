<script>
    function swapTheme(){
        console.log("swap theme");
        const html = document.querySelector('html');
        const currentTheme = html?.getAttribute("data-theme");
        if(currentTheme === "dark") {
            html?.setAttribute("data-theme", "light");
        } else {
            html?.setAttribute("data-theme", "dark");
        }
    }
</script>

<header>
    <nav class="container">
        <ul><li><a href="/">Home</a></li></ul>
        <ul><li><a href="/character/create">Create a Character</a></li></ul>
    </nav>
</header>

<div class="theme-switcher" on:keydown={swapTheme}>
    <i class="switcher"></i>
</div>

<slot />


<style>
    :root {
        --transition: 0.2s ease-in-out;
    }

    .theme-switcher {
        position: fixed;
        bottom: 1rem;
        right: 1rem;
        z-index: 1000;
        cursor: pointer;

        width: auto;
        background-color: white;
        color: black;
        margin-bottom: 0;
        padding: .75rem;
        border-radius: 2rem;
        line-height: 1;
        text-align: right;
        max-width: 100%;
        transition: 
            background-color var(--transition),
            border-color var(--transition),
            color var(--transition),
            box-shadow var(--transition);
    }

    .theme-switcher:hover::before{
        content: "Turn dark mode off ";
    }
    
    .switcher::after{
        display: inline-block;
        width: 1rem;
        height: 1rem;
        background-color: black;
        color: black;
        border: .15rem solid currentColor;
        border-radius: 50%;
        background: linear-gradient(to right,currentColor 0,currentColor 50%,transparent 50%);
        content: "";
        vertical-align: bottom;
        transition: transform var(--transition);
    }
</style>