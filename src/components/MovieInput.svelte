<script>
 import { createEventDispatcher } from 'svelte';

 const dispatch = createEventDispatcher();
 let title='';
 let rating=1;
 
 const onTitleChange=(e)=>{
     title=e.target.value;
 }
 const onRatingSelect=(e)=>{
     rating=e.target.value;
 }
 const submitMovie = () =>{
     if(title){
        dispatch('submitMovie', {
            movie:{
                title,
                rating
            }
        });
        title = '';
        rating = 1;
     }
 }
</script>


<div class="movie__input">
   <input 
      type="text"
      placeholder="Movie Title" 
      value={title}
      on:keyup={onTitleChange}
      />
    <!-- svelte-ignore a11y-no-onchange -->
    <select value={rating} on:change={onRatingSelect}>
       <option value={1}>1</option>
       <option value={2}>2</option>
       <option value={3}>3</option>
       <option value={4}>4</option>
       <option value={5}>5</option>
    </select>
    <button on:click={submitMovie} disabled={!title}>Add Movie</button>
</div>

<style>
  .movie__input{
    width: 100%;
    display: flex; 
  }
  input{
      flex: 1;
      margin: 0;
  }
  .movie__input select{
      width: 75px;
      margin: 0 10px;
  }
  .movie__input button{
      margin: 0;
  }
</style>