<script lang="ts">
    import { page } from '$app/stores';
    import { navItems } from '$lib/navItems.js';
    // console.log($page.url.pathname);
</script>

<div class="container-fluid">
    <div class="row">
        <div class="col-3 col-md-2">
<h2><a href="/" class="text-decoration-none">Nota Eksamensbestillinger</a></h2>
<nav>
    <ul class="list-group">
        <li>
            <a href="ubehandlede" class="list-group-item list-group-item-action active" aria-current="true">
            Bestillinger</a>
            <ul class="list-unstyled list-group-item">
                <li><a href="arkiv" class="border-0 list-group-item list-group-item-action text-body text-decoration-none d-block py-1">Arkiv</a></li>
                <li><a href="slettede" class="border-0 list-group-item list-group-item-action text-body text-decoration-none d-block py-1">Slettede</a></li>
            </ul>   
        </li>
      <li><a href="eksamener" class="list-group-item list-group-item-action">Eksamener</a></li>
      <li><a href="statistik" class="list-group-item list-group-item-action">Statistik</a></li>
      <li><a href="fakturering" class="list-group-item list-group-item-action">Fakturering</a></li>
      <li><a href="rush_hour" class="list-group-item list-group-item-action">Rush hour</a></li>
      <li><a href="dubletter" class="list-group-item list-group-item-action">Dubletter</a></li>
      <li><a href="udtraek" class="list-group-item list-group-item-action">Udtræk</a></li>
    </ul>
</nav>
</div>
<div class="col-9 col-md-10">
    <div class="d-flex flex-wrap my-2">
        <h1>Bestillinger</h1>
        <form class="d-flex ms-auto" role="search">
            <input class="form-control me-2" type="search" placeholder="Søg i bestillinger" aria-label="Search">
            <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
    </div>
    <nav class="navbar navbar-expand-sm bg-body-tertiary">
  <div class="container-fluid">
    <!-- <a class="navbar-brand" href="#">Navbar</a> -->
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarToggler" aria-controls="navbarToggler" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarToggler">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0 flex-wrap ">
        {#each navItems as navItem, i}
            <li class="nav-item">
                {#if $page.url.pathname === "/" + navItem.slug}
                    <a class="nav-link active" href="{navItem.slug}" aria-current="page">
                            {navItem.title} {#if navItem.count}({navItem.count}){/if}
                    </a>
                {:else}                
                    <a class="nav-link" href="{navItem.slug}">
                        {navItem.title} {#if navItem.count}({navItem.count}){/if}
                    </a>
                {/if}
            </li>
        {/each}

<!--         <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li> -->
      </ul>
    </div>
  </div>
</nav>




<main>
    <slot />
</main>
</div><!-- cols -->
</div><!-- .row -->
</div><!-- .container-fluid -->