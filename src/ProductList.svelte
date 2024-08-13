<script>
    // @ts-nocheck
    
    import { Link } from 'svelte-routing';
    
    export let products = [];
    
    let categories = [];
    let selectedCategory = '';
    let sortOrder = '';
    
    const fetchCategories = async () => {
      const res = await fetch('https://fakestoreapi.com/products/categories');
      categories = await res.json();
    };
    
    const handleCategoryChange = (/** @type {{ target: { value: string; }; }} */ event) => {
      selectedCategory = event.target.value;
    };
    
    const handleSortChange = (/** @type {{ target: { value: string; }; }} */ event) => {
      sortOrder = event.target.value;
    };
    
    $: filteredProducts = products
      .filter(product => selectedCategory ? product.category === selectedCategory : true)
      .sort((a, b) => sortOrder === 'low-to-high' ? a.price - b.price : sortOrder === 'high-to-low' ? b.price - a.price : 0);
    
    fetchCategories();
    </script>
