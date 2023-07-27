<script lang="ts">
    import { onMount } from 'svelte';
    import { tabItems } from '$lib/tabItems.js';

    onMount(()=>{
        document.querySelector("#ubehandlede-tab").click(); 
    })    
</script>

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
