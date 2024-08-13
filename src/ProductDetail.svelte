<script>
  import { onMount } from 'svelte';
  import { Link } from 'svelte-routing';

  export let params = {}; // Route parameters passed from the parent component
  let product = null;
  let productId = params.id || ''; // Extract productId from params

  const fetchProduct = async () => {
    try {
      const res = await fetch(`https://fakestoreapi.com/products/${productId}`);
      if (res.ok) {
        product = await res.json();
      } else {
        console.error('Failed to fetch product');
      }
    } catch (error) {
      console.error('Error fetching product:', error);
    }
  };

  onMount(() => {
    fetchProduct();
  });
</script>

<style>
  .product-detail {
    max-width: 100%; /* Ensures the container can use the full width of the screen */
    margin: 0 auto;
    text-align: center;
    font-weight: bold;
    padding: 1.5rem;
    background-color: #f9f9f9;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .product-detail img {
    max-width: 30%; /* Adjust the max-width to ensure the image fits within the container */
  }
  h1 {
    font-size: 2rem;
    margin-bottom: 0.5rem;
    color: #333;
  }
  p {
    font-size: 1rem;
    margin: 0.5rem 0;
    color: #555;
  }
  .price {
    font-weight: bold;
    color: #1a202c;
  }
   

  /* Responsive adjustments for smaller screens */
@media (max-width: 600px) {
  .product-detail {
    width: 100%;
  }
}
</style>

{#if product}
  <div class="product-detail">
    <img src={product.image} alt={product.title} class="product-image" />
    <h1>{product.title}</h1>
    <p class="price">${product.price}</p>
    <p>Category: {product.category}</p>
    <p>Ratings: {product.rating.rate} (Based on {product.rating.count} reviews)</p>
    <p>{product.description}</p>
    <Link to="/" class="back-button">Back to Products</Link>
  </div>
{:else}
  <p>Loading...</p>
{/if}
