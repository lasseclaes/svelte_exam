<div class="row">
    <h3>Old nav</h3>
        <nav class="navbar navbar-expand-sm bg-body-tertiary">
    <!-- <a class="navbar-brand" href="#">Navbar</a> -->
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarToggler" aria-controls="navbarToggler" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarToggler">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0 flex-wrap ">
        {#each tabItems as navItem, i}
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
        {/each}</ul>
        </div>
    </nav>

</div>

<!--      <li>
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
      <li><a href="udtraek" class="list-group-item list-group-item-action">Udtræk</a></li> -->