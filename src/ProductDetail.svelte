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
