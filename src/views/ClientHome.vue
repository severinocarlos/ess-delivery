<template>
  <div class="clienthome bg-[#261918] min-h-screen relative">
    <NavBar /> <!-- NavBar dos componentes-->
    <div class="absolute left-40 top-32"> <!-- Button "Meus Pedidos"-->
      <button type="button" @click='goToOrderHistory()' class="focus:outline-none text-white bg-[#541F1B] hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-l px-7 py-3 mr-10 mb-2">Meus pedidos</button>
    </div>

    <div class= "absolute right-72 top-32"> <!-- Search Bar, onde muda o tamanho é em pl-10 na linha 15, e na linha 8 define a posição, relativa a div da linha 2-->
      <form>   
        <label for="default-search" class="mb-2 text-sm font-medium text-gray-900 sr-only ">Search</label>
        <div class="relative">
            <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                <svg aria-hidden="true" class="w-5 h-5 text-gray-500 " fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
            </div>
            <input type="search" id="default-search" class="block w-100 p-10 pl-10 text-sm py-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 " placeholder="Search..." required>
            <button type="submit" class="text-white absolute right-2.5 bottom-2.5 bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-4 py-2 ">Search</button>
        </div>
    </form>
    </div>

      <!-- Botão "Carrinho"-->
    <button  @click='goToShoppingCart()' type="submit" class=" hover:bg-red-800 focus:ring-4 absolute right-32 top-32 focus:outline-none bg-[#A62C21]  focus:ring-red-300 font-medium rounded-lg text-l inline-block px-6 py-1 mr-10 mb-2 ">
        <img src="@\assets\img\carrinho.png" alt="Carrinho de Compras" class=" h-10 w-11" >
    </button>

    <!-- Cards dos restaurantes e das comidas-->
    <div class=" mx-auto max-w-6xl justify-center px-6 md:flex md:space-x-7 xl:px-0 pt-52" >
      <!-- Botão dos restaurantes -->
        <div @click="goToRestaurants()">
          <button class="focus:outline-none focus:ring-4 focus:ring-red-300">  
            <img src="@\assets\img\restaurantes.png" alt="Descrição da imagem" style="width: 550px;" class="rounded-lg transform hover:scale-105 transition duration-300"> <!-- fica um pouco maior quando passa o mouse por cima-->
          </button> 
        </div>
      
      <!-- Botão das comidas -->
        <div>
          <button class="focus:outline-none focus:ring-4 focus:ring-red-300">  
            <img src="@\assets\img\comidas.png" alt="Descrição da imagem" style="width: 550px;" class="rounded-lg transform hover:scale-105 transition duration-300"> <!-- fica um pouco maior quando passa o mouse por cima-->
          </button> 
        </div>
    </div>

    <!-- Segundo restaurante -->
    <div class="text-xl font-bold text-white px-28 py-3"> Bode do Nô </div>
    <div class=" flex flex-wrap items-center space-x-12 justify-center py-4 bg-cover inset-x-0  " > <!-- Flexbox do cardápio de pratos-->
      <div v-for="dish in dishes_1" :key="dish.id">
        <button class=" w-56 h-56 bg-[#541F1B] border-gray-200 rounded-lg shadow transform hover:scale-105 transition duration-300 " @click="addToCart(dish)">
          <a href="#">
            <img :src="dish.url" :alt="dish.nome" class= 'object-scale-down h-28 w-full mx-auto block'>
          </a>
          <div class="px-5 pb-5">
              <a href="#">
                  <h5 class="text-lg font-semibold tracking-tight text-white ">{{dish.nome}}</h5>
              </a>
              <div class="text-xs text-white">{{dish.descricao}} </div>
              <div class="flex items-center justify-between p-1">
                  <div class="text-xl font-bold text-white">{{dish.preco}} </div>
                  <a href="#" class="text-white bg-blue-700   font-medium rounded-lg text-sm px-1 py-1.5 text-center ">Add to cart</a>
              </div>
            </div>
          </button>
      </div>
    </div>
      
    <!-- Segundo restaurante -->
    <div class="text-xl font-bold text-white px-28 py-3"> Ratão Burguer </div>
    <div class="flex flex-wrap items-center space-x-12 justify-center py-4 bg-cover inset-x-0" > <!-- Flexbox do cardápio de pratos-->
      <div v-for="dish in dishes_2" :key="dish.id">
        <button class=" w-56 h-56 bg-[#541F1B] border-gray-200 rounded-lg shadow transform hover:scale-105 transition duration-300" @click="addToCart(dish)">
          <a href="#">
            <img :src="dish.url" :alt="dish.nome" class= 'object-scale-down h-28 w-full mx-auto block'>
          </a>
          <div class="px-5 pb-5">
              <a href="#">
                  <h5 class="text-lg font-semibold tracking-tight text-white ">{{dish.nome}}</h5>
              </a>
              <div class="text-xs text-white">{{dish.descricao}} </div>
              <div class="flex items-center justify-between p-1">
                  <div class="text-xl font-bold text-white">{{dish.preco}} </div>
                  <a href="#" class="text-white bg-blue-700   font-medium rounded-lg text-sm px-1 py-1.5 text-center ">Add to cart</a>
              </div>
          </div>
        </button>
      </div>
    </div>

    <!-- Avisar ao usuário que só pode adicionar itens de um mesmo restaurante no carrinho -->
    <div v-if="this.not_compatible">
        <div class="modal fixed w-full h-full top-0 left-0 flex items-center justify-center">
          <div class="modal-overlay absolute w-full h-full bg-gray-900 opacity-50"></div>
              <div class="modal-container bg-white w-[300px] mx-auto h-[175px] rounded-[20px] shadow-lg z-50 overflow-y-auto">
                  <div class="modal-content py-4 text-left px-6">
                      <div class="modal-body mt-2">
                          <!-- Conteúdo do modal aqui -->
                        <div class="text-center font-bold">
                            <p>Só é possível acrescentar ao carrinho itens de um mesmo restaurante!</p>
                        </div>
                        <div class="flex justify-center">
                        <button @click="closeModal" class="bg-[#9DBF69] hover:bg-[#A62C21] rounded-lg text-sm px-9 py-2.5 mt-7" >
                          Voltar
                        </button>
                        </div>
                      </div>
                  </div>
              </div>
        </div>
    </div>
    
  </div>
</template>
  
<script>
  import NavBar from '@/components/NavBar.vue'
  import axios from 'axios';

  export default {
    name: 'ClientHome',
    components: {
      NavBar,
    },
    data() {
    return {
      dishes_1: [],
      dishes_2: [],
      cart: [],
      found: false,
      not_compatible: false
    }
  },
  async mounted() {
    await axios.get('http://localhost:3000/clienthome1')
      .then(response => {
        this.cart = [...response.data];
      })
      .catch(error=> {
        console.error(error);
      });
    axios.get('http://localhost:3000/clienthome_first_restaurant')
      .then(response => {
        this.dishes_1 = response.data;
      })
      .catch(error => {
        console.error(error);
      });
    axios.get('http://localhost:3000/clienthome_second_restaurant')
      .then(response => {
        this.dishes_2 = response.data;
      })
      .catch(error => {
        console.error(error);
      });
      console.log(this.cart)
  },
    methods:{
      goToShoppingCart() {
      this.$router.push('/shoppingcart');
      },
      goToOrderHistory() {
      this.$router.push('/order-history');
      },
      goToRestaurants() {
        this.$router.push('/restaurants-list')
      },
      update(){
        console.log('updated')
        axios.get('http://localhost:3000/clienthome1')
        .then(response => {
          this.cart = [...response.data];
        })
        .catch(error=> {
          console.error(error);
        });
      },
      addToCart(dish) {
        this.update();
        console.log('addToCart')

        // Se o carrinho estiver vazio, somente acrescenta o item nele
        if (this.cart.length == 0){

          axios.post('http://localhost:3000/clienthome',  {nome: dish.nome, descricao: dish.descricao, preco: dish.preco, url: dish.url, quantidade: 1, restaurante: dish.restaurante}  )
          .then(response => {
            console.log(response.data.message);
            location.reload();
          })
          .catch(error => {
            console.error(error);
          });
        }
        else { // Se o carrinho não estiver vazio
          let i = 0;
          let index = 0;

          this.cart.forEach((doc) => {
            if (doc.restaurante !== dish.restaurante){ // Se o item adicionado for de outro restaurante, aparece o aviso
              this.not_compatible = true;
            }
            if (doc.nome == dish.nome){  // Ativa o found se já houver o item que será adicionado no carrinho
              console.log('Está no carrinho')
              index = i;
              this.found = true; 
            }
            i = i + 1;
          });

          // Se o item for do mesmo restaurante
          if (!this.not_compatible){ 
            if (!this.found){ // Se não houver outro do mesmo item no carrinho
              console.log('not found');
              axios.post('http://localhost:3000/clienthome',  {nome: dish.nome, descricao: dish.descricao, preco: dish.preco, url: dish.url, quantidade: 1, restaurante: dish.restaurante}  )
              .then(response => {
                console.log(response.data.message);
                location.reload();
              })
              .catch(error => {
                console.error(error);
              });
            }

            if (this.found){ // Se houver outro do mesmo item no carrinho, acrescenta uma unidade na quantidade (chama o put)
              console.log('found');
              axios.put('http://localhost:3000/clienthome2',  {nome: dish.nome, index: index}  )
              .then(response => {
                console.log(response.data.message);
                location.reload();
              })
              .catch(error => {
                console.error(error);
              });
            }
          }
      }
      this.found = false;
      // location.reload();
      },
      closeModal(){
        this.not_compatible = false;
      }
    }
  }
</script>


