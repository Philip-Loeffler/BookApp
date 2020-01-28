<script>
import Book from './Book.svelte'
import Button from './Button.svelte'
let title = '';
let pages = 0;
let description = '';
let books =[]

function setTitle(event) {
	title = event.target.value;
}

function addBook() {
    const newBook = {
        title : title,
        pages : pages,
        description : description

    };
    books = books.concat(newBook)
}

</script>

<style>
    h1 {
        color: purple;
        
    }
    section{
        margin: auto;
        width :30rem;
        
    }
    label,input,textarea{width: 100%}
</style>

<div>
<label for="title">Title</label>
<input types='text' value={title} on:input={setTitle}/>
</div>

<div>
<label for="pages">Pages</label>
<input type="numbers" value={pages} bind:value={pages}/>
</div>

<div>
<label for ="description">Description</label>
<textarea rows="3" id="description" bind:value={description}/>
</div>

<!-- we are dynamically setting values from the inputs, 
then those values are being passed to the book app
and are displayed as such -->
<Button on:click={addBook}>ADD Book</Button>

{#if books.length === 0} 
<p>
add a new book
</p>
{:else}
{#each books as book}
<Book
bookTitle={book.title}
bookPages={book.pages}
bookDescription={book.description}/>
{/each}
{/if}


