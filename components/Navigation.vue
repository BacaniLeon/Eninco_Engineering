<template>
    <nav :class="[{navBar__MobileMenu: menuHidden}, 'navBar']">
    <div class="img_div">
        <NuxtLink to="/" class="navBar__LogoLink"><img src="../public/resources/images/logo.png" class="LogoLink"></NuxtLink>
        <img src="../public/resources/images/menu.png" class="navBar__Menu" @click="showMenu">
    </div>
        <ul>
            <li><NuxtLink to="/" @click="changeOverflow()">Home</NuxtLink></li>
            <li><NuxtLink to="/products" @click="changeOverflow()" >Products</NuxtLink></li>
            <li><NuxtLink to="/about" @click="changeOverflow()">About</NuxtLink></li>
            <li><NuxtLink to="/news" @click="changeOverflow()">News</NuxtLink></li>
            <li><NuxtLink to="/contact" @click="changeOverflow()">Contact</NuxtLink></li>
        </ul>
    </nav>
  </template>
  
  <script setup>
  
  const menuHidden = ref(false);
  const showMenu = computed(() => {
   menuHidden.value=!menuHidden.value;
   if(menuHidden.value===true){
    var htmlElement = document.querySelector("html");
    htmlElement.style.overflow="hidden";
   }
   if(menuHidden.value===false){
    var htmlElement = document.querySelector("html");
    htmlElement.style.overflow="visible";
   }
  })
  
  function changeOverflow(){
    var htmlElement = document.querySelector("html");
    htmlElement.style.overflow='visible';
  }
    
  
    
  </script>
  