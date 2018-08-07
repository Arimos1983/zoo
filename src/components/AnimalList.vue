<template>
  <div >
      <tr v-for="animal in animals" :key="animal.name">
          <td>{{animal.name}}</td>
          <td>{{animal.species}}</td>
          <td>{{animal.yearOfBirth}}</td>
      </tr>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',

    data()
    {
        return {

            animals: [
                {name: "Pera", species: "Lav", yearOfBirth: "2001" },
                {name: "Mile", species: "Delfin", yearOfBirth: "2007" },
                {name: "Milica", species: "Zebra", yearOfBirth: "2011" },
                {name: "Jovan", species: "Soko", yearOfBirth: "2015" },
                {name: "Snesko", species: "Polarni medved", yearOfBirth: "1998" },
            ]

        };
    }
  
}
</script>

