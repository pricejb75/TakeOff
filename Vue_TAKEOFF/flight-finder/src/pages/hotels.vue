<script>
import UtilitiesService from '../services/UtilitiesService';

export default {
  name: "Hotels",
  component: {
    UtilitiesService
  },
  data() {
    return {
      hotelPreferencesDto: {
        iataCode: "",
        city: "",
        adults: 0,
        checkIn: "",
        checkOut: "",
      }
    };
  },
  methods: {
    seePossibleDestinationOptions() {
      this.$store.commit("SET_HOTEL_PREFERENCES_DTO", this.hotelPreferencesDto);
      // @TODO what if the user pressed search without entering anything?
      this.$router.push({ name: 'PossibleDestinations', params: {keyword: this.hotelPreferencesDto.city}});
    }
  }
};
</script>

<template>
  <div class="hotel-search-container">
    <div class="background-image-container-hotel">
      <div class="hotel-search">
        <h1 class="hotel-search-h1">Find Hotels with your Flight</h1>
        <h3 class="hotel-search-h3">Create a Package and Save</h3>
      </div>
      <div class="search-box-hotel">
        <i class="uil uil-users-alt"></i>
        <input
          id="number-guests-form-hotel"
          type="number"
          min="1"
          placeholder="Select Number Of Guests"
          v-model="hotelPreferencesDto.adults"
          required
        />
      </div>
      <div class="search-box-hotel">
        <i class="uil uil-compass"></i>
        <input
          id="city-state-form-hotels"
          type="text"
          placeholder="City/State"
          v-model="hotelPreferencesDto.city"
          required
        />
      </div>
     
      <div class="search-box-hotel">
        <i class="uil uil-bed-double"></i>
        <input type="date" placeholder="Checking in.." v-model="hotelPreferencesDto.checkIn" required />
      </div>
      
      <div class="search-box-hotel">
        <i class="uil uil-luggage-cart"></i>
        <input type="date" placeholder="Checking out.." v-model="hotelPreferencesDto.checkOut" required />
      </div>

      <form id="search-hotels-form">
          <button @click="seePossibleDestinationOptions">
            Search Hotels
          </button>
      </form>

    </div>
  </div>
</template>

<style scoped>
:root {
  --primary-color: #0038ff;
  --secondary-color: #85c4ff;
  --third-color: #ffffff;
  --fourth-color: #000000;
  --fifth-color: #e0e0e0;
  --sixth-color: #db0f0f;
  --seventh-color: #8a2020;
  --eighth-color: #ffc107;
}

* {
  box-sizing: border-box;
}

.hotel-search-container {
  background-color: var(--fifth-color);
  height: 100vh;
  display: flex;
  text-align: center;
  justify-content: space-around;
  align-items: stretch;
}

.background-image-container-hotel {
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url(hotel2_vojtech-bruzek-Yrxr3bsPdS0-unsplash.jpg);
  background-position: right center;
  background-repeat: repeat;
  background-size: cover;
  width: 100%;
}

.hotel-search {
  padding-top: 10em;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  flex-direction: column;
  padding-bottom: 2em;
}

.search-box-hotel {
  background-color: white;
  border-radius: 12px;
  border-color: var(--fourth-color);
  display: flex;
  align-items: center;
  padding-left: 10px;
  height: 50px;
  width: 400px;
  margin: 1em auto;
}

.hotel-search-h1 {
  color: var(--third-color);
  text-align: center;
  font-size: 3rem;
}

.hotel-search-h3 {
  color: red;
  text-align: center;
  font-size: 2rem;
}

#number-guests-form-hotel {
  width: 100%;
}

.uil-users-alt {
  font-size: 2rem;
  color: black;
}

.uil-compass {
  font-size: 2rem;
  color: black;
}

.uil-bed-double {
  font-size: 2rem;
  color: black;
}

.uil-luggage-cart {
  font-size: 2rem;
  color: black;
}

.search-hotels {
  background-color: var(--primary-color);
  border-radius: 12px;
  border-color: var(--primary-color);
  display: flex;
  height: 50px;
  width: 430px;
  align-self: center;
  justify-content: center;
  align-items: center;
  font-size: 1rem;
  margin: 1em auto;
}

.search-hotels:hover {
  color: var(--secondary-color);
  background-color: var(--primary-color);
  border: 2px solid var(--secondary-color);
}

#search-hotels-form > button{
  width: 400px;
  background-color: var(--primary-color);
  border-radius: 10px;
  padding: .5em;
  margin-bottom: 1em;
}

#search-hotels-form > button:hover {
  color: var(--secondary-color);
  border: 1px solid var(--secondary-color);
}

a {
  background-color: var(--sixth-color);
  padding: .5em;
  border-radius: 10px;
}

a:hover {
  color: var(--eighth-color);
}
</style>
