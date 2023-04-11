<script>
    import { onMount } from "svelte";

    onMount(() => {
        const html = document.querySelector('html');
        const themeSwitcher = document.getElementById("theme-switcher");

        html?.setAttribute("data-theme", "dark");
        
        function swapTheme(){
            const currentTheme = html?.getAttribute("data-theme");
            const themeSelection = currentTheme === "dark" ? "light" : "dark";
            html?.setAttribute("data-theme", themeSelection);
        }

        themeSwitcher?.addEventListener("click", swapTheme);
    });
</script>

<header>
    <nav class="container">
        <ul><li><a href="/">Home</a></li></ul>
        <ul><li><a href="/character/create">Create a Character</a></li></ul>
    </nav>
</header>

<div class="theme-switcher" id="theme-switcher">
    <i class="switcher"></i>
</div>

<slot />

<style>
    :root {
        --transition: 0.2s ease-in-out;
        --primary: rgb(121, 22, 220);
        --primary-hover: rgb(82, 15, 148);
        --primary-focus: rgb(94, 15, 173);
        --primary-inverse: #FFF;

        --form-element-active-border-color: var(--primary);
        --form-element-focus-color: var(--primary-focus);
        --switch-color: var(--primary-inverse);
        --switch-checked-background-color: var(--primary);
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