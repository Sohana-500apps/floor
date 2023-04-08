<template>
     <!-- start of showing Floor in the table -->
     <div class="overflow-auto">
        <table class="shadow-2xl border-2 border-gray-800 w-full">
         <thead class="bg-gray-800 text-white text-left">
             <tr>
                 <th class="py-3">Name</th>
                 <th class="py-3">BuildArea</th>
                 <th class="py-3">CarpetArea</th>
                 <th class="py-3">Facing</th>
                 <th class="py-3">BedRoom</th>
                 <th class="py-3">BathRooms</th>
                 <th class="py-3">Kitchens</th>
                 <th class="py-3">Balconies</th>
                 <th class="py-3">Edit Action</th>
                 <th class="py-3">Delete Action</th>
             </tr>
         </thead>
         <tbody class="divide-y  divide-gray-800">
             <tr v-for="(floor,index) in FloorUrlData" :key="floor" class="text-left cursor-pointer">
               <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.name" class="focus:border-purple-500" cols="10" rows="1">{{floor.name}}</textarea>
                 <p v-else>{{floor.name}}</p>
               </td>
               <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.build_up_area" class="focus:border-purple-500" cols="10" rows="1">{{floor.build_up_area}}</textarea>
                 <p v-else>{{floor.build_up_area}}</p>
               </td>
               <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.carpet_area" class="focus:border-purple-500" cols="10" rows="1">{{floor.carpet_area}}</textarea>
                 <p v-else>{{floor.carpet_area}}</p>
               </td>
               <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.facing" class="focus:border-purple-500" cols="10" rows="1">{{floor.facing}}</textarea>
                 <p v-else>{{floor.facing}}</p>
               </td> 
               <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.bedrooms" class="focus:border-purple-500" cols="10" rows="1">{{floor.bedrooms}}</textarea>
                <p v-else>{{floor.bedrooms}}</p>
              </td>          
              <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.bathrooms" class="focus:border-purple-500" cols="10" rows="1">{{floor.bathrooms}}</textarea>
                <p v-else>{{floor.bathrooms}}</p>
              </td>  
              <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.kitchens" class="focus:border-purple-500" cols="10" rows="1">{{floor.kitchens}}</textarea>
                <p v-else>{{floor.kitchens}}</p>
              </td>  
              <td class="py-3 pr-6 whitespace-nowrap">
                <textarea v-if="editFloorIndex===index" v-model="editFloorForm.balconies" class="focus:border-purple-500" cols="10" rows="1">{{floor.balconies}}</textarea>
                <p v-else>{{floor.balconies}}</p>
              </td>  
               <td class="py-3 pr-6 whitespace-nowrap">
                 <CollectionFloorEdit @edit="editFloor(floor,index)"/>
               </td>
               <td class="py-3 pr-6 whitespace-nowrap">
                 <CollectionFloorDelete @delete="deleteFloor(floor)"/>
               </td>
             </tr>
         </tbody>
        </table>
           
     </div>
      <!-- End of showing Floor in the table -->
</template>
<script setup lang="ts">
//Defining the schema of Floorschema
interface FloorSchema{
  name:string,
  build_up_area:string,
  carpet_area:number,
  metric_name:string,
  facing:number,
  bedrooms:number
  bathrooms:number,
  kitchens:number,
  project_id:string,
  balconies:number
}
// Getting the props of FloorurlData
let props = defineProps<{ FloorUrlData:FloorSchema }>()
const emits = defineEmits(['edit','delete']);
const editFloorIndex=ref("0")


//Defining the schema of reactive FloorEditForm
interface FloorEditForm {
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
const editFloorForm:FloorEditForm=reactive({
  name:'',
  build_up_area:'',
  carpet_area:'',
  facing:'',
  bedrooms:'',
  bathrooms:'',
  kitchens:'',
  balconies:''
})

//Emitting the delete and pass it in the main
const deleteFloor=(floor:any)=>{
    emits('delete',floor)
  
}
//Emitting the edit and pass it in the main
const editFloor=(floor:any,index:any)=>{
    editFloorIndex.value=index
  emits('edit',floor,editFloorForm)
}
</script>