<template>
  <div >
      <form @submit.prevent >
          <input v-model="newAnimals.name" type="text" placeholder="name" > <br>
          <input v-model="newAnimals.species" type="text" placeholder="species"> <br>
          <input v-model="newAnimals.yearOfBirth" type="text" placeholder="year of birth"> <br>
          
          <select v-model="newAnimals.sector">
              <option v-for="sector in sectors" :key="sector.zona" v-bind:value="sector" >{{sector.zona}}</option>
          </select><br>
          
          <button @click="addAnimal" type="submit">Add animal</button>
      
      </form>

      <table>
        <tr v-for="(animal, key) in animals" :key="key" >
            <td>{{animal.name}}</td>
            <td>{{animal.species}}</td>
            <td v-if="animal.yearOfBirth != '' ">{{animal.yearOfBirth}}</td>
            <td v-else>{{'Unknown'}}</td>
            <td>{{animal.sector.zona}}</td>
            <td>
                <button @click="removeAnimal(animal)">Remove</button>
            </td>
            <td>
                <button @click="moveToTop(animal)">Move up</button>
            </td>
        </tr>
      </table>

      <table>
          <tr v-for="(sector, key) in sectors" :key="key">
            <td>{{sector.zona}}</td>
            <td>
            <button @click="bySector(sector)">Vidi listu životinja</button>
            </td>
          </tr>
      </table>

  </div>
</template>

<script>
const sectors = [
    {zona: "Mesojedi"},
    {zona: "biljojedi"},
    {zona: "Ptice"},
    {zona: "Vodene Zivotinje"}
]
export default {
  name: 'AnimalList',

    data()
    {
        return {
            color: "red",
            sectors: sectors,
            newAnimals: {},
            animals: [
                {id: 1,name: "Pera", species: "Lav", yearOfBirth: "2001", sector: sectors[0], background: true},
                {id: 2,name: "Mile", species: "Delfin", yearOfBirth: "2007", sector: sectors[3], background: false},
                {id: 3,name: "Milica", species: "Zebra", yearOfBirth: "2011", sector: sectors[1], background: false},
                {id: 4,name: "Jovan", species: "Soko", yearOfBirth: "", sector: sectors[2], background: true},
                {id: 5,name: "Snesko", species: "Polarni medved", yearOfBirth: "1998", sector: sectors[0], background:false},
            ]

        };
    },

    methods: 
    {
        removeAnimal(animal)
        {
            let animalToDelete = this.animals.indexOf(animal);
            this.animals.splice(animalToDelete,1);
        },
        moveToTop(animal)
        {
            let animalToMove = this.animals.indexOf(animal);
            this.animals.splice(animalToMove,1);
            this.animals.unshift(animal);
        },
        addAnimal()
        {
            this.animals.push(this.newAnimals);
            this.newAnimals = {};
        },
        bySector(sector)
        {   
            
            const animalsList=[];
            this.animals.forEach(animal => {
            if (animal.sector && animal.sector.zona === sector.zona) 
            {
                animalsList.push(`${animal.name} ${animal.species}`);
            }
            });
            alert(animalsList.toString());
            
        }

    }
    
  
};
</script>

