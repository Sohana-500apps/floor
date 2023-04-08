<template>
    <div>
        <!-- start of Floor -->
       <div class="p-[50px] flex divide-y-2 border-y">
           
        <h1>Floors</h1>
        <!-- start of add button -->
        <div class="ml-[56rem]">
            <button class="flex bg-slate-100" @click="openFloor">
            <PlusIcon class="h-6 w-6"/>
            <p class="ml-3">Add Floor</p>
            </button>
        </div>
          <!-- end of add button -->
            <!-- opening the Floor modal by clicking add Floor -->
        <CollectionFloorAdd v-show="isFloor" @cancel="isFloor=false" @save="saveFloor"/>
       </div>
    <div class="text-center" v-if="!isFloor">
        <h1 class="text-3xl">Floors List</h1>
         <div>
            <CollectionFloorList   :FloorUrlData="FloorUrlData" @delete="deleteFloorListener" @edit="editFloorListener"/>
        </div>
      </div>
    </div> 
     <!-- End of Floor -->
</template>
<script setup lang="ts">
//importing the HeroIcon and  useAuthLazyFetch
import { PlusIcon } from "@heroicons/vue/24/outline"
import {useAuthLazyFetch}  from "../../../composables/useAuthLazyFetch"




//Define the schema of FloorUrl
interface FloorUrl{
    FloorUrl:string,
    url:string
}
// Get the props of FloorUrl and url
const props = withDefaults(defineProps<FloorUrl>(), {
    FloorUrl: "",
    url:""
})

//Showing the dynamic Floor in the table
const getFloorUrl = async () => {
    try {
    const { data: FloorData } = await useAuthLazyFetch(props.FloorUrl, {});
    return FloorData;
  } catch (error) {
    console.error("Error fetching tag URL", error);
    return null;
  }
}
const FloorUrlData = await getFloorUrl();

const isFloor=ref(false)
////opening the  Add model
const openFloor=()=>{
    isFloor.value=!isFloor.value
}
//saving the Floor

const saveFloor=(addFloorForm)=>{

useAuthLazyFetchPost(`${props.url}/`, {
    body: {
    name:addFloorForm.name,
    build_up_area:addFloorForm.buildingarea,
    carpet_area:addFloorForm.carpetarea,
    metric_name:"Hello",
    facing:addFloorForm.facing,
    bedrooms:addFloorForm.bedroom,
    bathrooms:addFloorForm.bathroom,
    kitchens:addFloorForm.kitchen,
    project_id:"string",
    balconies:addFloorForm.balconies
    }
  });
}

//Deleting the floor
const deleteFloorListener=(floor)=>{

if(confirm('Are you sure to delete this record?')){
    useAuthLazyFetchDelete(`${props.url}/${floor.uid}`, {});
    let floorurlIndex=FloorUrlData.value.findIndex(item => item.uid === floor.uid)
    console.log("floorurl",FloorUrlData)
    if(floorurlIndex!==-1){
        FloorUrlData.value.splice(floorurlIndex,1)
    }
}
}
//Editing the Floor

const editFloorListener=(floor,editFloorForm)=>{
 useAuthLazyFetchPut(`${props.url}/${floor.uid}?name=${editFloorForm.name}&build_up_area=${editFloorForm.build_up_area}&carpet_area=${editFloorForm.carpet_area}&facing=${editFloorForm.facing}&bedrooms=${editFloorForm.bedrooms}&bathrooms=${editFloorForm.bathrooms}&kitchens=${editFloorForm.kitchens}&balconies=${editFloorForm.balconies}`, {
    body: {
      name:editFloorForm.name,
      build_up_area:editFloorForm.build_up_area,
      carpet_area:editFloorForm.carpet_area,
      metric_name:floor.metric_name,
      facing:editFloorForm.facing,
      bedrooms:editFloorForm.bedrooms,
      bathrooms:editFloorForm.bathrooms,
      kitchens:editFloorForm.kitchens,
      project_id:floor.project_id,
      balconies:editFloorForm.balconies
    },
  });
}

</script>