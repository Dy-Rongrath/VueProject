<template>

  <div class="min-h-screen bg-white flex flex-col justify-center items-center">

    <div class="flex items-center justify-between bg-white py-6 px-2 w-full max-w-[1586px] mx-auto">
      <!-- SearchBox and MenuItems -->
      <img src="../assets/image/Logo.svg" alt="logo">
      <searchbox></searchbox>
      <div class="flex space-x-4">
        <MenuItem menuName="Account" icon="bx-user" />
        <MenuItem menuName="Compare" icon="bx-recycle" />
        <MenuItem menuName="Wishlist" icon="bx-heart" />
        <MenuItem menuName="Cart" icon="bx-cart" />
      </div>
    </div>

    <!-- Meneu & Categories -->
    <div class="w-full max-w-[1586px] mx-auto">
      <show-case></show-case>
      <Menu topic="Featured Categories" @menu-selected="handleMenuSelection"></Menu>
      <category :activeMenu="activeMenu"></category>
    </div>

    <!-- Promotion -->
    <div class="w-full max-w-[1586px] mx-auto my-8">
      <promotion></promotion>
    </div>

    <!-- Menu & Products -->
    <div class="w-full max-w-[1586px] mx-auto">
      <Menu topic="Popular Products" @menu-selected="handleMenuSelection"></Menu>
      <product></product>
    </div>

  </div>

</template>

<script>
import ShowCase from '@/components/ShowCase.vue';
import MenuItem from '@/components/MenuItem.vue';
import Searchbox from '@/components/Searchbox.vue';
import Category from '@/components/Category.vue';
import Promotion from '@/components/Promotion.vue';
import Menu from '@/components/Menu.vue';
import Product from '@/components/Product.vue';

export default {
  name: "home",
  components: {
    Menu,
    Category,
    Promotion,
    Product,
    ShowCase,
    MenuItem,
    Searchbox,
  },
  data() {
    return {
      activeMenu: 1
    }
  },
  methods: {
    handleMenuSelection(menuId) {
      this.activeMenu = menuId;
    }
  }
}
</script>
