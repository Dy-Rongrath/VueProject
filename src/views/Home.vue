<template>

  <div class="min-h-screen bg-white flex flex-col justify-center items-center">

    <div class="flex items-center justify-between bg-white py-6 px-2 w-full max-w-[1586px] mx-auto">

      <!-- Logo -->
      <img src="../assets/image/Logo.svg" alt="logo">

      <!-- SearchBox -->
      <searchbox></searchbox>

      <!-- Menu -->
      <div class="flex space-x-4">
        <MenuItem menuName="Account" icon="bx-user" />
        <MenuItem menuName="Compare" icon="bx-recycle" />
        <MenuItem menuName="Wishlist" icon="bx-heart" />
        <MenuItem menuName="Cart" icon="bx-cart" />
      </div>

    </div>

    <div class="flex justify-between items-center mb-6 w-full max-w-[1586px] mx-auto border-y-2 py-4">

      <!-- Dropdown Category -->
      <div class="flex items-center space-x-3">
        <ul class="flex items-center space-x-3 list-none">
          <li class="flex justify-center items-center text-center space-x-1 bg-green-500 w-64 h-11 rounded-md px-4">
            <i class='bx bx-grid-alt text-xl'></i>
            <span>Browse all categories</span>
            <i class='bx bx-chevron-down text-xl'></i>
          </li>
        </ul>
      </div>

      <!-- Menu -->
      <RouterLink to="" class="flex gap-6">
        <MenuItem menuName="Hot Deals" icon="bxs-hot" icon_color="#3BB77E" font_weight="700" />
        <MenuItem menuName="Home" dropList="none" font_weight="700" />
        <MenuItem menuName="Food" dropList="yes" font_weight="700" />
        <MenuItem menuName="Vegetables" dropList="yes" font_weight="700" />
        <MenuItem menuName="Drink" dropList="none" font_weight="700" />
        <MenuItem menuName="Cookies" dropList="none" font_weight="700" />
        <MenuItem menuName="Meat & Seafood" dropList="yes" font_weight="700" />
        <MenuItem menuName="Bakery" dropList="none" font_weight="700" />
      </RouterLink>

      <!-- Contact -->
      <div class="flex items-end space-x-2">
        <div class="flex items-center text-3xl">
          <i class='bx bx-headphone'></i>
        </div>
        <div class="flex flex-col text-end">
          <div class="text-xl text-green-500 font-extrabold">099 777 888</div>
          <div class="text-xs">24/7 support center</div>
        </div>
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
