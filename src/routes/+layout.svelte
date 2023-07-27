<script>
    import { page } from '$app/stores';
    import { navItems } from '$lib/navItems.js';
    $: classesActive = (href) => '/' + href ===  $page.url.pathname ? 'active' : '';
    $: ariaCurrent = (href) => '/' + href === $page.url.pathname ? 'true' : 'false';
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
            <slot />
        </div><!-- cols -->
    </div><!-- .row -->
</div><!-- .container-fluid -->