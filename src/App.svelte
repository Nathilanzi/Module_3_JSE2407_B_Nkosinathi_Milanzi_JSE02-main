<script>
  import { Router, Route } from 'svelte-routing';
  import Header from './Header.svelte';
  import ProductList from './ProductList.svelte';
  import ProductDetail from './ProductDetail.svelte';
  import { onMount } from 'svelte';

  let products = []; // Assume you have a way to fetch and pass products to ProductList

  // Fetch products (for demonstration purposes)
  const fetchProducts = async () => {
    const res = await fetch('https://fakestoreapi.com/products');
    products = await res.json();
  };

  onMount(() => {
    fetchProducts();
  });
</script>
