<template>
  <div>
    <div class="bg-gradient-to-b from-[#261918] to-[#A62C21]">
      <div class="bg-no-repeat bg-fixed md:grid md:grid-cols-7 md:gap-5"
           style="background-image: url('img/restaurant_update_bg.png');
                  background-position: right">
        <div class="md:col-start-2 md:col-span-4 mt-5 md:mt-0">
          <br>
          <form action="#" method="POST">
            <div class="flex flex-col justify-center items-center">
              <div class="shadow sm:overflow-hidden sm:rounded-md w-full">
                <div class="space-y-6 bg-gray-50 px-4 py-5 sm:p-6">
                  <br>
                  <div class="grid grid-cols-11 gap-6">
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <h2 class="text-4xl font-bold leading-10 text-gray-800">Responsável da loja</h2>
                    </div>
                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <p class="mt-1 text-sm text-gray-700">Atualize os dados da pessoa que tem o nome no contrato social da empresa.</p>
                    </div>
                  </div>
                  <br>
                  <br>
                  <div class="grid grid-cols-11 gap-6">                     
                    <div class="col-span-11 sm:col-start-2 sm:col-span-9">
                      <div class="relative">
                        <input type="text" id="nome" v-model="restaurant.nome" :disabled="!editing[0]" @input="onlyLetters" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="nome" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Nome Completo</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="cpf" v-model="restaurant.cpf" :disabled="!editing[0]" v-mask="['###.###.###-##']" required pattern="\d{3}\.\d{3}\.\d{3}-\d{2}" class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="cpf" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">CPF</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="rg" v-model="restaurant.rg" :disabled="!editing[0]" v-mask="['#.###.###']" required pattern="\d{1}.\d{3}.\d{3}" class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="rg" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">RG</label>
                      </div>
                    </div>
                  
                  </div>
                </div>
                <div class="bg-gray-200 flex justify-between px-4 py-3 text-right sm:px-6">
                  <button @click="toggleEditing(0)" type="button" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">{{ editing0 ? 'Cancelar' : 'Editar' }}</button>
                  <button @click="verifyInput(0)" type="submit" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">Salvar</button>                
                </div>
              </div>
                  
<!--///////////////////////////////////////////////////-->

              <br>
              <div class="shadow sm:overflow-hidden sm:rounded-md w-full">
                <div class="space-y-6 bg-gray-50 px-4 py-5 sm:p-6">    
                  <br>
                  <div class="grid grid-cols-11 gap-6">
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <h2 class="text-4xl font-bold leading-10 text-gray-800">Informações da loja</h2>
                    </div>
                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <p class="mt-1 text-sm text-gray-700">Atualize com os dados do seu negócio.</p>
                    </div>
                  </div>
                  <br>
                  <br>
                  <div class="grid grid-cols-11 gap-6">                    
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="razao_social" v-model="restaurant.razao_social" :disabled="!editing[1]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="razao_social" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Razão Social</label>
                      </div>
                      <div v-if="razao_social_failure" @mousemove="hideText()" class="group flex w-full justify-center rounded-b-lg bg-gray-100 p-1">
                        <p class="text-[#83271F] text-[12px] font-bold text-center">Razão social já cadastrada</p>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="nome_loja" v-model="restaurant.nome_loja" :disabled="!editing[1]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="nome_loja" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Nome da Loja</label>
                      </div>
                      <div v-if="nome_loja_failure" @mousemove="hideText()" class="group flex w-full justify-center rounded-b-lg bg-gray-100 p-1">
                        <p class="text-[#83271F] text-[12px] font-bold text-center">Nome da loja já cadastrado</p>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="tel" id="telefone" v-model="restaurant.telefone" :disabled="!editing[1]" v-mask="['(##) #####-####']" required pattern="\(\d{2}\) \d{5}-\d{4}" class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" "/>
                        <label for="telefone" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Telefone</label>
                      </div>
                      <div v-if="telefone_failure" @mousemove="hideText()" class="group flex w-full justify-center rounded-b-lg bg-gray-100 p-1">
                        <p class="text-[#83271F] text-[12px] font-bold text-center">Telefone já cadastrado</p>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">   
                      <div class="relative">
                        <input type="text" id="especialidade" v-model="restaurant.especialidade" :disabled="!editing[1]" @input="onlyLetters" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="especialidade" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Especialidade</label>
                      </div>   
                    </div>
                               
                  </div>
                </div>
                <div class="bg-gray-200 flex justify-between px-4 py-3 text-right sm:px-6">
                  <button @click="toggleEditing(1)" type="button" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">{{ editing1 ? 'Cancelar' : 'Editar' }}</button>
                  <button @click="verifyInput(1)" type="submit" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">Salvar</button>                
                </div>
              </div>
                  
<!--///////////////////////////////////////////////////-->
              
              <br>
              <div class="shadow sm:overflow-hidden sm:rounded-md w-full">
                <div class="space-y-6 bg-gray-50 px-4 py-5 sm:p-6">    
                  <br>
                  <div class="grid grid-cols-11 gap-6">
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <h2 class="text-4xl font-bold leading-10 text-gray-800">Endereço da loja</h2>
                    </div>
                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <p class="mt-1 text-sm text-gray-700">Atualize com as informações de endereço da sua loja.</p>
                    </div>
                  </div>
                  <br>
                  <br>
                  <div class="grid grid-cols-11 gap-6">                     
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="cep" v-model="restaurant.cep" :disabled="!editing[2]" v-mask="['#####-###']" required pattern="\d{5}-\d{3}" class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="cep" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">CEP</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <div class="relative">
                        <select id="estado_uf" v-model="restaurant.estado_uf" :disabled="!editing[2]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" >
                          <option disabled selected>---</option>
                          <option value="AC">Acre</option>
                          <option value="AL">Alagoas</option>
                          <option value="AP">Amapá</option>
                          <option value="AM">Amazonas</option>
                          <option value="BA">Bahia</option>
                          <option value="CE">Ceará</option>
                          <option value="DF">Distrito Federal</option>
                          <option value="ES">Espírito Santo</option>
                          <option value="GO">Goiás</option>
                          <option value="MA">Maranhão</option>
                          <option value="MT">Mato Grosso</option>
                          <option value="MS">Mato Grosso do Sul</option>
                          <option value="MG">Minas Gerais</option>
                          <option value="PA">Pará</option>
                          <option value="PB">Paraíba</option>
                          <option value="PR">Paraná</option>
                          <option value="PE">Pernambuco</option>
                          <option value="PI">Piauí</option>
                          <option value="RJ">Rio de Janeiro</option>
                          <option value="RN">Rio Grande do Norte</option>
                          <option value="RS">Rio Grande do Sul</option>
                          <option value="RO">Rondônia</option>
                          <option value="RR">Roraima</option>
                          <option value="SC">Santa Catarina</option>
                          <option value="SP">São Paulo</option>
                          <option value="SE">Sergipe</option>
                          <option value="TO">Tocantins</option>
                        </select>
                        <label for="estado_uf" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">UF</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="cidade" v-model="restaurant.cidade" :disabled="!editing[2]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="cidade" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Cidade</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="bairro" v-model="restaurant.bairro" :disabled="!editing[2]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="bairro" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Bairro</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-2 sm:col-span-9">
                      <div class="relative">
                        <input type="adress" id="endereco" v-model="restaurant.endereco" :disabled="!editing[2]" autocomplete="street-address" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="endereco" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Endereço</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="numero" v-model="restaurant.numero" :disabled="!editing[2]" v-mask="['######']" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="numero" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Número</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="complemento" v-model="restaurant.complemento" :disabled="!editing[2]" class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="complemento" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Complemento</label>
                      </div>
                    </div>
                   
                  </div>            
                </div>
                <div class="bg-gray-200 flex justify-between px-4 py-3 text-right sm:px-6">
                  <button @click="toggleEditing(2)" type="button" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">{{ editing2 ? 'Cancelar' : 'Editar' }}</button>
                  <button @click="verifyInput(2)" type="submit" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">Salvar</button>                
                </div>
              </div>

<!--///////////////////////////////////////////////////-->              

              <br>
              <div class="shadow sm:overflow-hidden sm:rounded-md w-full">
                <div class="space-y-6 bg-gray-50 px-4 py-5 sm:p-6">
                  <br>
                  <div class="grid grid-cols-11 gap-6">
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <h2 class="text-4xl font-bold leading-10 text-gray-800">Dados de serviços</h2>
                    </div>
                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <p class="mt-1 text-sm text-gray-700">Preencha com as informações de funcionamento da sua loja.</p>
                    </div>
                  </div>
                  <br>
                  <br>
                  <div class="grid grid-cols-11 gap-6">                     
                    <div class="col-span-11 sm:col-start-2 sm:col-span-4">
                      <div class="relative">
                        <input type="text" id="taxa" v-model="restaurant.taxa" v-mask="['R$ ##']" :disabled="!editing[3]" required pattern="R\$ [1-9][0-9]*" class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
                        <label for="taxa" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Taxa de entrega</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-7 sm:col-span-4">
                      <div class="relative">
                        <select id="tempo_entrega" v-model="restaurant.tempo_entrega" :disabled="!editing[3]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" >
                          <option disabled>---</option>
                          <option value="10min-20min">De 10min a 20 min</option>
                          <option value="15min-30min">De 15min a 30min</option>
                          <option value="30min-45min">De 30min a 45min</option>
                          <option value="45min-1h">De 45min a 1h</option>
                        </select>
                        <label for="tempo_entrega" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Tempo de entrega</label>
                      </div>
                    </div>

                    <div class="col-span-11 sm:col-start-4 sm:col-span-5">
                      <div class="relative">
                        <select id="horario" v-model="restaurant.horario" :disabled="!editing[3]" required class="block rounded-t-lg px-2.5 pb-2.5 pt-5 w-full text-sm text-gray-900 bg-gray-100 dark:bg-gray-700 border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" >
                          <option disabled>---</option>
                          <option value="08h-17h">Das 08h às 17h</option>
                          <option value="08h-12h">Das 08h às 12h</option>
                          <option value="12h-18h">Das 12h às 18h</option>
                          <option value="14h-00h">Das 14h às 00h</option>
                          <option value="17h-22h">Das 17h às 22h</option>
                        </select>
                        <label for="horario" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-4 z-10 origin-[0] left-2.5 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-4">Horário de funcionamento</label>
                      </div>
                    </div>
                  
                  </div>
                </div>
                <div class="bg-gray-200 flex justify-between px-4 py-3 text-right sm:px-6">
                  <button @click="toggleEditing(3)" type="button" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">{{ editing3 ? 'Cancelar' : 'Editar' }}</button>
                  <button @click="verifyInput(3)" type="submit" class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">Salvar</button>                
                </div>
              </div>

            </div>
            <br>
          </form>
        </div>
      </div>
    </div> 
  </div>
</template>

<script scoped>
import {mask} from 'vue-the-mask'
import axios from 'axios';

export default {
  name: 'UpdateRegisterView',
  directives: {mask},
  props: {
    msg: String
  },
  data() {
    return {
      restaurant: {
        nome: '',
        cpf: '',
        rg: '',
        razao_social: '',
        nome_loja: '',
        telefone: '',
        especialidade: '',
        cep: '',
        estado_uf: '',
        cidade: '',
        bairro: '',
        endereco: '',
        numero: '',
        complemento: '',
        taxa: '',
        tempo_entrega: '',
        horario: '',
        original: {},
      },
      editing: [false, false, false, false],
      editing0: false,
      editing1: false,
      editing2: false,
      editing3: false,
      razao_social_failure: false,
      telefone_failure: false,
      nome_loja_failure: false,
    }
  },
  created() {
    axios.get('http://localhost:3000/update-register')
      .then(response => {
        this.restaurant = {...response.data, original: {...response.data}};
        
      })
      .catch(error => {
        console.error(error);
      });
  },
  methods: {
    onlyLetters() {
      this.restaurant.nome = this.restaurant.nome.replace(/[^a-zA-ZÀ-ú\s]/g, ''),
      this.restaurant.especialidade = this.restaurant.especialidade.replace(/[^a-zA-ZÀ-ú\s]/g, '')
    },
    toggleEditing(index) {
      this.editing = this.editing.map((value, i) => i === index ? !value : value);
      
      if (index === 0) {
        this.editing0 = !this.editing0;
        if (!this.editing[index]) {
          this.restaurant.nome = this.restaurant['original']['nome'];
          this.restaurant.cpf = this.restaurant['original']['cpf'];
          this.restaurant.rg = this.restaurant['original']['rg'];
        }
      } else if (index === 1) {
        this.editing1 = !this.editing1;
        if (!this.editing[index]) {
          this.restaurant.razao_social = this.restaurant['original']['razao_social'];
          this.restaurant.nome_loja = this.restaurant['original']['nome_loja'];
          this.restaurant.telefone = this.restaurant['original']['telefone'];
          this.restaurant.especialidade = this.restaurant['original']['especialidade'];
        }
      } else if (index === 2) {
        this.editing2 = !this.editing2;
        if (!this.editing[index]) {
          this.restaurant.cep = this.restaurant['original']['cep'];
          this.restaurant.estado_uf = this.restaurant['original']['estado_uf'];
          this.restaurant.cidade = this.restaurant['original']['cidade'];
          this.restaurant.bairro = this.restaurant['original']['bairro'];
          this.restaurant.endereco = this.restaurant['original']['endereco'];
          this.restaurant.numero = this.restaurant['original']['numero'];
          this.restaurant.complemento = this.restaurant['original']['complemento'];
        }
      } else if (index === 3) {
        this.editing3 = !this.editing3;
        if (!this.editing[index]) {
          this.restaurant.taxa = this.restaurant['original']['taxa'];
          this.restaurant.tempo_entrega = this.restaurant['original']['tempo_entrega'];
          this.restaurant.horario = this.restaurant['original']['horario'];
        }
      }
    },
    submit(index) {
      event.preventDefault();
      if (index == 0) {
        if (this.restaurant['original']['nome'] != this.restaurant.nome ||
            this.restaurant['original']['cpf'] != this.restaurant.cpf ||
            this.restaurant['original']['rg'] != this.restaurant.rg) {

          axios.put('http://localhost:3000/update-register/0', {
            nome: this.restaurant.nome,
            cpf: this.restaurant.cpf,
            rg: this.restaurant.rg
          });
          this.restaurant['original']['nome'] = this.restaurant.nome;
          this.restaurant['original']['cpf'] = this.restaurant.cpf;
          this.restaurant['original']['rg'] = this.restaurant.rg;
                
          this.editing[index] = !this.editing[index];
          this.editing0 = !this.editing0;
        }
      } else if (index == 1) {
        if (this.restaurant['original']['razao_social'] != this.restaurant.razao_social ||
            this.restaurant['original']['nome_loja'] != this.restaurant.nome_loja ||
            this.restaurant['original']['telefone'] != this.restaurant.telefone ||
            this.restaurant['original']['especialidade'] != this.restaurant.especialidade) {

          axios.put('http://localhost:3000/update-register/1', {
            razao_social: this.restaurant.razao_social,
            nome_loja: this.restaurant.nome_loja,
            telefone: this.restaurant.telefone,
            especialidade: this.restaurant.especialidade
          });
          this.restaurant['original']['razao_social'] = this.restaurant.razao_social;
          this.restaurant['original']['nome_loja'] = this.restaurant.nome_loja;
          this.restaurant['original']['telefone'] = this.restaurant.telefone;
          this.restaurant['original']['especialidade'] = this.restaurant.especialidade;
          
          this.editing[index] = !this.editing[index];
          this.editing1 = !this.editing1;
        }
      } else if (index == 2) {
        if (this.restaurant['original']['cep'] != this.restaurant.cep ||
            this.restaurant['original']['estado_uf'] != this.restaurant.estado_uf ||
            this.restaurant['original']['cidade'] != this.restaurant.cidade ||
            this.restaurant['original']['bairro'] != this.restaurant.bairro ||
            this.restaurant['original']['endereco'] != this.restaurant.endereco ||
            this.restaurant['original']['numero'] != this.restaurant.numero ||
            this.restaurant['original']['complemento'] != this.restaurant.complemento) {

          axios.put('http://localhost:3000/update-register/2', {
            cep: this.restaurant.cep,
            estado_uf: this.restaurant.estado_uf,
            cidade: this.restaurant.cidade,
            bairro: this.restaurant.bairro,
            endereco: this.restaurant.endereco,
            numero: this.restaurant.numero,
            complemento: this.restaurant.complemento
          });
          this.restaurant['original']['cep'] = this.restaurant.cep;
          this.restaurant['original']['estado_uf'] = this.restaurant.estado_uf;
          this.restaurant['original']['cidade'] = this.restaurant.cidade;
          this.restaurant['original']['bairro'] = this.restaurant.bairro;
          this.restaurant['original']['endereco'] = this.restaurant.endereco;
          this.restaurant['original']['numero'] = this.restaurant.numero;
          this.restaurant['original']['complemento'] = this.restaurant.complemento;
          
          this.editing[index] = !this.editing[index];
          this.editing2 = !this.editing2;
        }
      } else if (index == 3) {
        if (this.restaurant['original']['taxa'] != this.restaurant.taxa ||
            this.restaurant['original']['tempo_entrega'] != this.restaurant.tempo_entrega ||
            this.restaurant['original']['horario'] != this.restaurant.horario) {
            
          axios.put('http://localhost:3000/update-register/3', {
            taxa: this.restaurant.taxa,
            tempo_entrega: this.restaurant.tempo_entrega,
            horario: this.restaurant.horario
          });

          this.restaurant['original']['taxa'] = this.restaurant.taxa;
          this.restaurant['original']['tempo_entrega'] = this.restaurant.tempo_entrega;
          this.restaurant['original']['horario'] = this.restaurant.horario;
                
          this.editing[index] = !this.editing[index];
          this.editing3 = !this.editing3;
        }
      }
    },
    async verifyData(index) {
      event.preventDefault();
      try {
        let response;
        if (index == 0) {
          this.submit(index);
        } else if (index == 1) {
          response = await axios.post('http://localhost:3000/verify-data/1', {
            razao_social: this.restaurant.razao_social,
            telefone: this.restaurant.telefone,
            nome_loja: this.restaurant.nome_loja,
          });

          this.razao_social_failure = false;
          this.nome_loja_failure = false;
          this.telefone_failure = false;

          if (response.data === "Razão social já cadastrado") {
            this.razao_social_failure = true;
            return;
          } else if (response.data === "Telefone já cadastrado") {
            this.telefone_failure = true;
            return;
          } else if (response.data === "Nome da loja já cadastrado") {
            this.nome_loja_failure = true;
            return;
          } else if (response.data === "Razão social e telefone já cadastrado") {
            this.razao_social_failure = true;
            this.telefone_failure = true;
            return;
          } else if (response.data === "Razão social e nome da loja já cadastrado") {
            this.razao_social_failure = true;
            this.nome_loja_failure = true;
            return;
          } else if (response.data === "Nome da loja e telefone já cadastrado") {
            this.nome_loja_failure = true;
            this.telefone_failure = true;
            return;
          } else if (response.data === "Razão social, nome da loja e telefone já cadastrado") {
            this.razao_social_failure = true;
            this.nome_loja_failure = true;
            this.telefone_failure = true;
            return;
          } else if (response.data === "Razão social, nome da loja e telefone não existem") {
            this.razao_social_failure = false;
            this.nome_loja_failure = false;
            this.telefone_failure = false;
            this.submit(index);
          }
        } else if (index == 2) {
          this.submit(index);
        } else if (index == 3) {
          this.submit(index);
        }
      } catch (error) {
        console.error(error);
      }
    },
    verifyInput(index) {
      const cpfRegex = /^\d{3}\.\d{3}\.\d{3}-\d{2}$/
      const rgRegex = /^\d{1}.\d{3}.\d{3}$/
      const telRegex = /^\(\d{2}\) \d{5}-\d{4}$/
      const cepRegex = /^\d{5}-\d{3}$/
      
      if (index == 0 && (!this.restaurant.nome || !this.restaurant.cpf || !this.restaurant.rg)) {
        return;
      } else if (index == 1 && (!this.restaurant.razao_social || !this.restaurant.nome_loja || !this.restaurant.telefone || !this.restaurant.especialidade)) {
        return;
      } else if (index == 2 && (!this.restaurant.cep || !this.restaurant.estado_uf || !this.restaurant.cidade || !this.restaurant.bairro || !this.restaurant.endereco || !this.restaurant.numero)) {
        return;
      } else if (index == 3 && (!this.restaurant.taxa || !this.restaurant.tempo_entrega || !this.restaurant.horario)) {
        return;
      }

      if (index == 0 && (!cpfRegex.test(this.restaurant.cpf) || !rgRegex.test(this.restaurant.rg))) {
        return;
      } else if (index == 1 && !telRegex.test(this.restaurant.telefone)) {
        return;
      } else if (index == 2 && !cepRegex.test(this.restaurant.cep)) {
        return;
      }

      this.verifyData(index);

    },
    hideText() {
      this.razao_social_failure = false;
      this.telefone_failure = false;
      this.nome_loja_failure = false;
    },
    
  }

}
</script>
