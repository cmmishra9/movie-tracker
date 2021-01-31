<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    export let searchTerm='';

    const search = event =>{
        searchTerm=event.target.value;
        if(searchTerm){
            dispatch('search', {
                searchTerm
            })
        }else{
            dispatch('clearSearch', {})
        }
    }
</script>

<input 
type="text"
placeholder="Search Your Movie"
value={searchTerm}
on:keyup={search}
>

<style>
 input{
     width: 100%;
 }
</style>