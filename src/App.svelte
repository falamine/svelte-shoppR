<script>
    import {Pages} from './Nav';
    import Home from "./Home.svelte";
    import Product from "./Product.svelte";

    let currentPage = Pages.Home;

    function goTo(page) {
        currentPage = page;
    }
</script>
<div class="container-fluid">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="home">ShoppR</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <button class="btn-light" on:click={_=> goTo(Pages.Home)}>Home</button>
                </li>
                <li class="nav-item">
                    <button class="btn-light" on:click={_=> goTo(Pages.Product)}>Products</button>
                </li>
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        Dropdown
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                        <a class="dropdown-item" href="#">Action</a>
                        <a class="dropdown-item" href="#">Another action</a>
                        <div class="dropdown-divider"></div>
                        <a class="dropdown-item" href="#">Something else here</a>
                    </div>
                </li>
                <li class="nav-item">
                    <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
                </li>
            </ul>
            <div><a class="nav-link" href="#">
                <i class="fas fa-shopping-cart"></i>
            </a>
            </div>
            <form method="post" action="/api/product/search" class="form-inline my-2 my-lg-0">
                <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" name="name">
                <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Find Products</button>
            </form>
        </div>
    </nav>

    <div>
        {#if currentPage === Pages.Home}
            <Home/>
        {:else if currentPage === Pages.Product}
            <Product/>
        {:else}
            Default
        {/if}

    </div>

</div>

