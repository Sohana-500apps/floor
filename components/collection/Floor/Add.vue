<template>
    <!-- start of Add Floor Form field -->
      <div class="fixed z-10 inset-0 overflow-y-auto">
          <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
            <div class="fixed inset-0 transition-opacity" aria-hidden="true">
              <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
            </div>
      
            <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full">
              <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
               
          
          
                <form class="w-full max-w-sm">
                  <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-name">
                       Name
                      </label>
                    </div>
                    <div class="md:w-2/3">
                      <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-name" type="text" v-model="addFloorForm.name" required>
                    </div>
                  </div>
                  <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-buildingarea">
                       BuildArea
                      </label>
                      </div>
                      <div class="md:w-2/3">
                        <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-buildingarea" type="number" v-model="addFloorForm.buildingarea" required>
                      </div>
                  </div>
                  <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-carpetarea">
                       CarpetArea
                      </label>
                      </div>
                      <div class="md:w-2/3">
                        <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-carpetarea" type="number" v-model="addFloorForm.carpetarea" required>
                      </div>
                  </div>
                  <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-facing">
                       Facing
                      </label>
                      </div>
                      <div class="md:w-2/3">
                        <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-facing" type="text" v-model="addFloorForm.facing" required>
                      </div>
                  </div>
                  <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-bedroom">
                       BedRoom
                      </label>
                      </div>
                      <div class="md:w-2/3">
                        <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-bedroom" type="number" v-model="addFloorForm.bedroom" required>
                      </div>
                  </div>
                 <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-type">
                       BathRooms
                      </label>
                      </div>
                      <div class="md:w-2/3">
                        <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-name" type="number" v-model="addFloorForm.bathroom" required>
                      </div>
                  </div> 
                  <div class="md:flex md:items-center mb-6">
                    <div class="md:w-1/3">
                      <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-kitchen">
                       kitchens
                      </label>
                      </div>
                      <div class="md:w-2/3">
                        <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-kitchen" type="number" v-model="addFloorForm.kitchen" required>
                      </div>
                  </div> 
                  <div class="md:flex md:items-center mb-6">
                  <div class="md:w-1/3">
                    <label class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-balconies">
                     Balconies
                    </label>
                  </div>
                  <div class="md:w-2/3">
                    <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-" type="number" v-model="addFloorForm.balconies" required>
                  </div>
                </div>
                </form>
              </div>
              <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                <button type="button" class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-green-600 text-base font-medium text-white hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 sm:ml-3 sm:w-auto sm:text-sm" @click="saveFloor">
                  Save
                </button>
                <button type="button" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm" @click="cancelFloor">
                  Cancel
                </button>
              </div>
            </div>
          </div>
        </div>
        <!-- End of Add Floor Form field -->
  </template>
  <script setup lang="ts">
  const emits = defineEmits(['cancel','save']);
  //Defining the schema of reactive FloorForm
interface FloorForm {
  name:string,
  build_up_area:number,
  carpet_area:number,
  facing:string,
  bedrooms:number,
  bathrooms:number,
  kitchens:number,
  balconies:number,
  
}
//Declaring in the empty form and use it in v-model
  let addFloorForm:FloorForm=reactive({
   name:'',
   buildingarea:'',
   carpetarea:'',
   facing:'East',
   bedroom:'',
   bathroom:'',
    kitchen:'',
    balconies:''
  })
  //Emitting the cancel  and pass it in main
  const cancelFloor=()=>{
  emits('cancel')
  }
  //Emitting the save and pass it in the main and resetting the value
  const saveFloor=()=>{
  console.log("add",addFloorForm)
    emits('save',addFloorForm)
    addFloorForm.name=''
    addFloorForm.buildingarea=0
    addFloorForm.carpetarea=0
    addFloorForm.facing=''
    addFloorForm.bedroom=0
    addFloorForm.bathroom=0
    addFloorForm.kitchen=0
    addFloorForm.balconies=0
  }
  </script>