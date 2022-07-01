<script setup>
defineProps({
  name: {
    type: String,
    required: true
  },
  year: {
    type: Number,
    required: true
  },
  month: {
    type: Number,
    required: true
  },
  color: {
    type: String,
    required: true
  },
  image: {
    type: String,
    required: true
  },
  imageRatio: {
    type: String
  },
  fact: {
    type: String,
    required: true
  }
})

const calcAge = (year, month) => {
    const today = new Date();
    const thisYear = today.getFullYear();
    const thisMonth = today.getMonth() + 1;

    const catMonth = parseInt(month);
    const catYear = parseInt(year);

    // compare ages by subtracting year
    let ageYear = thisYear - catYear;
    let yearPlural = 's'
    let monthPlural = 's';
    
    let ageMonth;
    if (thisMonth - catMonth > 0) {
        ageMonth = thisMonth - catMonth
    } else {
        ageMonth = 12 - catMonth;
    }

    if (ageYear === 1) {
      yearPlural = '';
    }
    if (ageMonth === 1) {
      monthPlural = '';
    }
    return `${ageYear} year${yearPlural} ${ageMonth} month${monthPlural}`
}

 
</script>

<template>
  <div class="card">
    <div class="card-image">
        <img ref="catImage" :src="image" :alt="name" :class="imageRatio" />
    </div>
    <div class="card-content">
        <h3>{{ name }}</h3>
        <h4>{{ calcAge(year, month)}}</h4>
        <p>{{ color }}</p>
        <p><strong>Fun Fact:</strong> {{ fact }}</p>
    </div>
  </div>
</template>

<style>

h3, h4 {
  margin: 0;
  font-weight: 600;
}

.card {
    border-radius: .5rem;
    box-shadow: 0 0 1rem rgba(0,0,0,.15);
    overflow: hidden;
}

.card-image {
    height: 17rem;
    overflow: hidden;
}

.card-image img {
    object-fit: cover;
    object-position: center;
    width: 100%;
    height: 100%;
}

.card-image img.left {
    object-position: left;
}

.card-image img.right {
    object-position: right;
}

.card-content {
    padding: 1rem;
}

</style>