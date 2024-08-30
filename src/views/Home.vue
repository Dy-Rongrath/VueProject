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
      <div @click="toggleDropdown" class="relative">
        <button class="flex items-center bg-[#3BB77E] text-white py-2 px-4 rounded-md">
          <i class='bx bx-grid-alt pr-2'></i>
          {{ selectedCategory }}
          <i class='bx bx-chevron-down pl-2'></i>
        </button>
        <ul v-if="dropdownOpen" class="absolute z-10 bg-white shadow-lg w-48 mt-1">
          <li v-for="category in categories" :key="category.id" class="px-4 py-2 hover:bg-gray-100 cursor-pointer"
            @click="selectCategory(category)">
            {{ category.title }}
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
import { ref } from 'vue';

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
  },

  setup() {
    const categories = ref([
      { id: 1, title: 'All Categories' },
      { id: 2, title: 'Cake & Milk' },
      { id: 3, title: 'Peach' },
      { id: 4, title: 'Organic Kiwi' },
      { id: 5, title: 'Red Apple' },
      { id: 6, title: 'Snack' },
      { id: 7, title: 'Black Plum' },
      { id: 8, title: 'Vegetables' },
      { id: 9, title: 'Headphone' },
      { id: 10, title: 'Cake & Milk' },
      { id: 11, title: 'Orange' },
    ]);
    const selectedCategory = ref('Browse All Categories');
    const dropdownOpen = ref(false);

    const toggleDropdown = () => {
      dropdownOpen.value = !dropdownOpen.value;
    };

    const selectCategory = (category) => {
      selectedCategory.value = category.title;
      dropdownOpen.value = false;
    };

    return { categories, selectedCategory, dropdownOpen, toggleDropdown, selectCategory };
  }

}
</script>
