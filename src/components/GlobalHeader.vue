<template>
  <header class="header">
    <div class="header-content">
      <div class="left-section">
        <button class="icon-button" @click="toggleMenu">
          <span class="material-icons">menu</span>
        </button>
        <div class="company-name">LiveWell Marketing Corp.</div>
      </div>
      <router-link to="/home" class="logo-link">
        <h1 class="logo">Live Wellness</h1>
      </router-link>
      <div class="right-section">
        <nav class="main-nav">
          <div class="nav-item-container">
            <a href="#" @click.prevent="toggleShopDropdown" class="nav-item">
              Shop
              <span class="material-icons" :class="{ 'rotate': isShopDropdownOpen }">expand_more</span>
            </a>
            <div v-if="isShopDropdownOpen" class="dropdown-content">
              <a href="#" @click.prevent="handleLinkClick">
                <span class="material-icons">storefront</span> Our Products
              </a>
              <a href="#" @click.prevent="handleLinkClick">
                <span class="material-icons">shopping_cart</span> View Cart
              </a>
            </div>
          </div>
          <div class="nav-item-container">
          <a href="#" @click.prevent="toggleAccountDropdown" class="nav-item">
            Account
            <span class="material-icons" :class="{ 'rotate': isAccountDropdownOpen }">expand_more</span>
          </a>
          <div v-if="isAccountDropdownOpen" class="dropdown-content">
            <router-link to="/auth/register" @click="handleLinkClick">
              <span class="material-icons">person_add</span> Register
            </router-link>
            <router-link to="/auth/login" @click="handleLinkClick">
              <span class="material-icons">login</span> Login
            </router-link>
            <router-link to="/dashboard" @click="handleLinkClick">
              <span class="material-icons">dashboard</span> Dashboard
            </router-link>
          </div>
        </div>
        </nav>
        <button class="icon-button" @click="toggleSearch">
          <span class="material-icons">search</span>
        </button>
        <button class="icon-button" @click="openCart">
          <span class="material-icons">shopping_cart</span>
        </button>
      </div>
    </div>
    <div class="carousel" @touchstart="onTouchStart" @touchend="onTouchEnd">
      <div class="carousel-inner">
        <div class="carousel-item" v-for="item in items" :key="item.id">
          <img :src="item.image" :alt="item.title" />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import { useRouter } from 'vue-router'

export default {
  name: 'GlobalHeader',
  setup() {
    const router = useRouter()
    return { router }
  },
  data() {
    return {
      isMenuOpen: false,
      isShopDropdownOpen: false,
      isAccountDropdownOpen: false,
      isSearchOpen: false,
      startX: 0,
      items: [
        // Add your carousel items here
        // Example: { id: 1, image: 'path/to/image1.jpg', title: 'Image 1' },
      ]
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    toggleShopDropdown() {
      this.isShopDropdownOpen = !this.isShopDropdownOpen;
      this.isAccountDropdownOpen = false;
    },
    toggleAccountDropdown() {
      this.isAccountDropdownOpen = !this.isAccountDropdownOpen;
      this.isShopDropdownOpen = false;
    },
    closeDropdowns() {
      this.isAccountDropdownOpen = false;
      this.isShopDropdownOpen = false;
    },
    toggleSearch() {
      this.isSearchOpen = !this.isSearchOpen;
    },
    openCart() {
      // Implement cart opening logic
      this.handleLinkClick();
    },
    onTouchStart(event) {
      this.startX = event.touches[0].clientX;
    },
    onTouchEnd(event) {
      const endX = event.changedTouches[0].clientX;
      const distance = this.startX - endX;

      if (distance > 30) {
        console.log('Swiped Left');
      } else if (distance < -30) {
        console.log('Swiped Right');
      }
    },
    handleLinkClick() {
      this.closeDropdowns();
      this.$emit('link-clicked');
    }
  }
};
</script>

  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');
  @import url('https://fonts.googleapis.com/icon?family=Material+Icons');
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap');

  .carousel {
  overflow: hidden;
  position: relative;
}

.carousel-inner {
  display: flex;
  transition: transform 0.3s ease;
}

.carousel-item {
  min-width: 100%; /* Adjust as necessary */
  pointer-events: none; /* Prevent clicking */
}

.carousel-item img {
  width: 100%; /* Adjust to your design */
  height: auto;
}

  
  .header {
    background-color: #ffffff;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    padding: 0.75rem 2rem;
    font-family: 'Poppins', sans-serif;
  }
  
  .header-content {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .left-section, .right-section {
    display: flex;
    align-items: center;
    flex: 1;
  }
  
  .right-section {
    justify-content: flex-end;
  }
  
  .company-name {
    font-size: 0.9rem;
    font-weight: 400;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    max-width: 200px;
    margin-left: 1rem;
    color: #2c3e50;
  }
  
  .logo {
  font-size: 2.5rem;
  font-weight: 300; /* Thin and light */
  margin: 0;
  text-align: center;
  flex: 2;
  color: #2c3e50;
  font-family: 'Times New Roman', serif;
  font-weight: lighter;
}


  
  .main-nav {
    display: flex;
    margin-right: 1rem;
  }
  
  .nav-item-container {
  position: relative;
  margin-right: 1rem;
}

.nav-item {
  text-decoration: none;
  color: #2c3e50;
  font-weight: 400;
  display: flex;
  align-items: center;
  padding: 0.5rem 1rem;
  transition: background-color 0.3s ease;
  border-radius: 4px;
}

.nav-item:hover {
  background-color: #f0f8f0;
}

.dropdown-content {
  position: absolute;
  top: 100%;
  left: 0;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  border-radius: 4px;
  padding: 0.5rem 0;
  z-index: 1000;
  min-width: 250px;
}

.dropdown-content a {
  display: block;
  padding: 0.5rem 1rem;
  text-decoration: none;
  color: #2c3e50;
  transition: background-color 0.3s ease;
}

.dropdown-content a:hover {
  background-color: #f0f8f0;
}

.material-icons {
  margin-right: 0.5rem;
}

.rotate {
  transform: rotate(180deg);
}
  
  @media (max-width: 768px) {
    .header {
      padding: 0.5rem 1rem;
    }
  
    .company-name {
      max-width: 150px;
    }
  
    .logo {
      font-size: 2rem;
    }
  }
  </style>