<template>
  <div >
      <tr v-for="animal in animals" :key="animal.id">
          <td>{{animal.name}}</td>
          <td>{{animal.species}}</td>
          <td v-if="animal.yearOfBirth != '' ">{{animal.yearOfBirth}}</td>
          <td v-else>{{'Unknown'}}</td>
          <td>
              <button @click="removeAnimal(animal)">Remove</button>
          </td>
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
                {id: 1, name: "Pera", species: "Lav", yearOfBirth: "2001" },
                {id: 2,name: "Mile", species: "Delfin", yearOfBirth: "2007" },
                {id: 3,name: "Milica", species: "Zebra", yearOfBirth: "2011" },
                {id: 4,name: "Jovan", species: "Soko", yearOfBirth: "" },
                {id: 5,name: "Snesko", species: "Polarni medved", yearOfBirth: "1998" },
            ]

        };
    },

    methods: 
    {
        removeAnimal(animal)
        {
            let animalToDelete = this.animals.indexOf(animal);
            this.animals.splice(animalToDelete,1);
        }
    }
  
}
</script>

