<script lang="ts">
    import { page } from '$app/stores';
    import { navItems } from '$lib/navItems.js';
    $: classesActive = (href) => '/' + href ===  $page.url.pathname ? 'active' : '';
    $: ariaCurrent = (href) => '/' + href === $page.url.pathname ? 'true' : 'false';
    import { tabItems } from '$lib/tabItems.js';
    // console.log($page.url.pathname);
    //$: activeTab = (data_bs_target) => 
</script>

<div class="container-fluid">
    <div class="row">
        <div class="col-3 col-md-2">
<h2><a href="/" class="text-decoration-none">Nota <span class="h6">Eksamensbestillinger</span></a></h2>
<nav>
    <ul class="list-unstyled list-group">
        <li>   
            {#each navItems as navItem, i}
                         <a href="{navItem.slug}" class="list-group-item list-group-item-action {classesActive(navItem.slug)}" aria-current="{ariaCurrent(navItem.slug)}"> 
                            {navItem.title}
                        </a>
                        {#if navItem.submenu}
                            <ul class="list-unstyled list-group-item">
                                {#each navItem.submenu as submenu_item}
                                    <li>
                                        <a href="{submenu_item.subm_slug}" class="border-0 list-group-item list-group-item-action text-decoration-none d-block py-1 {classesActive(submenu_item.subm_slug)}">{submenu_item.subm_title}</a>
                                    </li>
                                {/each}
                            </ul>
                        {/if}
            {/each}
        </li>
   
    </ul>
</nav>
</div><!-- .cols -->
<div class="col-9 col-md-10">
    <div class="d-flex flex-wrap my-2">
        <h1>Bestillinger</h1>
        <form class="d-flex ms-auto" role="search">
            <input class="form-control me-2" type="search" placeholder="Søg i bestillinger" aria-label="Search">
            <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
    </div>
    <ul class="nav nav-tabs" id="myTab" role="tablist">
        {#each tabItems as tabItem}
            <li class="nav-item" role="presentation">
                <button class="nav-link" id="{tabItem.slug}-tab" data-bs-toggle="tab" data-bs-target="#{tabItem.slug}-tab-pane" type="button" role="tab" aria-controls="{tabItem.slug}-tab-pane" aria-selected="true">{tabItem.title}{#if tabItem.count}&nbsp;({tabItem.count}){/if}</button>
            </li>
        {/each} 
</ul>
<div class="tab-content" id="myTabContent">
    {#each tabItems as tabItem, i}
    <div class="tab-pane fade" id="{tabItem.slug}-tab-pane" role="tabpanel" aria-labelledby="{tabItem.slug}-tab" tabindex="{i + 1}">
        
    </div>
    {/each}
</div>


<main>
    <slot />
</main>
</div><!-- cols -->
</div><!-- .row -->
</div><!-- .container-fluid -->