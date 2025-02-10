<template>
  <Toast />
<div class="overflow-hidden rounded-lg bg-white shadow">
<div class="px-2 py-2 flex justify-start gap-3 " >

  <p class="text-blue-700">Statement For <br>{{ todaydate }} - {{ startdaydate }}</p>
  <button type="button" @click="customtoggle()"  class="rounded-md  px-2  text-sm font-semibold bg-indigo-500 text-white shadow-sm ring-1 ring-inset ring-gray-300"  >Customs</button>

  <div  v-if="customfilterbox" ref="customBox" class=" h-64 absolute z-10 border-2 border-gray-200 bg-white p-2 rounded-lg" style=" left: 42%; top: 19%; width: 400px;;">
    <div class="absolute bg-white border-l border-t border-gray-200 " style="width: 20px; height: 20px; ; transform: rotate(44deg) ; top: -11px; left:4%;"></div>
  
        <span class="text-lg"><i class="pi pi-clock"></i> Frequently used time period</span>
        <div class="w-full p-1 flex gap-2 pl-5">
          <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === 'week' }" class="rounded-md  px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLastWeek" >7 Days</button>
          <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === '15days' }" class="rounded-md   px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLast15Days">15 Days</button>
          <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === 'month' }" class="rounded-md  px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLastMonth">Month</button>
          <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === '3months' }" class="rounded-md  px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLast3Months">3Months</button>

        </div>

      <div class="mt-3">
        <span class="text-lg mt-3"><i class="pi pi-calendar"></i> DateRange Filter</span>
        <div class="w-full p-1 flex gap-2 pl-5" >
          <DatePicker v-model="dates" selectionMode="range" class="w-full" :manualInput="true" dateFormat="yy-mm-dd" showIcon @update:modelValue="handleDateChange" />
          <span>{{ myval }}</span>
        </div>
      </div>
  </div>






</div>
</div>

<div v-if="loading" class="w-full mt-5">
<div class="overflow-hidden rounded-lg bg-white shadow" >
<div class="px-12 py-2 flex animate-pulse">
 <div class="w-full p-1 flex" style="border-right: 2px solid rgb(189, 189, 189);">
   <div class="flex justify-center items-center p-1">
     <div class="h-12 w-12 bg-slate-300 rounded-full"></div>
   </div>
   <div class="w-full p-1">
     <div class="h-4 bg-slate-300 rounded w-2/3 mb-2"></div>
     <div class="h-6 bg-slate-300 rounded w-1/2"></div>
   </div>
 </div>
 <div class="w-full p-1 flex" style="border-right: 2px solid rgb(189, 189, 189);">
   <div class="flex justify-center items-center p-1">
     <div class="h-12 w-12 bg-slate-300 rounded-full"></div>
   </div>
   <div class="w-full p-1">
     <div class="h-4 bg-slate-300 rounded w-2/3 mb-2"></div>
     <div class="h-6 bg-slate-300 rounded w-1/2"></div>
   </div>
 </div>
 <div class="w-full p-1 flex" style="border-right: 2px solid rgb(189, 189, 189);">
   <div class="flex justify-center items-center p-1">
     <div class="h-12 w-12 bg-slate-300 rounded-full"></div>
   </div>
   <div class="w-full p-1">
     <div class="h-4 bg-slate-300 rounded w-2/3 mb-2"></div>
     <div class="h-6 bg-slate-300 rounded w-1/2"></div>
   </div>
 </div>
 <div class="w-full p-1 flex">
   <div class="flex justify-center items-center p-1">
     <div class="h-12 w-12 bg-slate-300 rounded-full"></div>
   </div>
   <div class="w-full p-1">
     <div class="h-4 bg-slate-300 rounded w-2/3 mb-2"></div>
     <div class="h-6 bg-slate-300 rounded w-1/2"></div>
   </div>
 </div>
</div>
</div>


<div class="space-y-4 p-4 mt-5" >
       <!-- Table Skeleton -->
       <div class="grid grid-cols-9 gap-4 animate-pulse">
         <!-- Rows -->
         <!-- Row 1 -->
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
     
         <!-- Row 2 -->
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
     
         <!-- Row 3 -->
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>

         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>

         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>

         <div class="col-span-9 grid grid-cols-9 gap-4">
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
           <div class="h-6 bg-gray-300 rounded col-span-1"></div>
         </div>
       </div>
     </div>
</div>


<div class="w-100" v-if="content">
 <div class="overflow-hidden rounded-lg bg-white shadow mt-1">
<div class="px-2 py-3 ">
 <ul role="list" class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-4">

<li class="col-span-1  rounded-lg bg-white shadow">
<div class="flex w-full items-center justify-between space-x-6 p-2">
<div class="flex truncate">
      <div class="flex justify-center items-center p-3 bg-indigo-50 rounded-full"  >
           <img src="https://cdn-icons-png.flaticon.com/128/16416/16416833.png" alt="" width="40" height="40">
       </div>
       <div class="w-full p-1" >
           <span class="text-slate-400 text-md">Invested Amount</span>
          <p class="text-slate-700"> <span><i class="pi pi-indian-rupee"></i></span> <span >{{ investamount }}</span></p>
       </div>
</div>
</div>
<div>

</div>
</li>

<li class="col-span-1 divide-y divide-gray-200 rounded-lg bg-white shadow">
<div class="flex w-full items-center justify-between space-x-6 p-2">
<div class="flex truncate">
 <div class="flex justify-center items-center p-3 bg-indigo-50 rounded-full"  >
           <img src="https://cdn-icons-png.flaticon.com/128/16416/16416833.png" alt="" width="40" height="40">
       </div>
       <div class="w-full p-1" >
           <span class="text-slate-400 text-md">Current Value</span>
          <p class="text-slate-700"><span><i class="pi pi-indian-rupee"></i></span> <span >{{ currentvalue }}</span></p>
       </div>
</div>
</div>
<div>

</div>
</li>


<li class="col-span-1 divide-y divide-gray-200 rounded-lg bg-white shadow">
<div class="flex w-full items-center justify-between space-x-6 p-2">
<div class="flex truncate">
 <div class="flex justify-center items-center p-3 bg-green-50 rounded-full"  >
           <img src="https://cdn-icons-png.flaticon.com/128/5501/5501360.png" alt="" width="40" height="40">
       </div>                
       <div class="w-full p-1" >
           <span class="text-slate-400 text-md">Overall Gain</span>
           <p  class="text-slate-700"> <span><i class="pi pi-indian-rupee"></i></span> <span >{{ overallgain }}</span></p>
       </div>
</div>
</div>
<div>

</div>
</li>

<li class="col-span-1 divide-y divide-gray-200 rounded-lg bg-white shadow">
<div class="flex w-full items-center justify-between space-x-6 p-2">
<div class="flex truncate">
 <div class="flex justify-center items-center p-3 bg-green-50 rounded-full"  >
           <img src="https://cdn-icons-png.flaticon.com/128/5501/5501360.png" alt="" width="40" height="40">
       </div>              
        <div class="w-full p-1" >
           <span class="text-slate-400 text-md">Today's Gain</span>
           <p  class="text-slate-700"> <span><i class="pi pi-indian-rupee"></i></span> <span >{{ todaygain }}</span></p>
        </div>

</div>
</div>
<div>

</div>
</li>

</ul>
</div>
</div>



<div class="overflow-hidden rounded-lg bg-white shadow mt-1">
<div class="px-2 py-3 ">
 <div class="card">
   <DataTable
     stripedRows
     ref="dt"
     v-model:filters="filters"
     :value="filteredCustomers"
     dataKey="id"
     filterDisplay="menu"
     scrollable
   
     paginator
     :rows="rows" 
     tableStyle="min-width: 20rem"
     :globalFilterFields="['stockname', 'quantity', 'avgprice', 'ltp', 'invamt', 'mktval', 'overall', 'days', 'date']"

   >

   <template #header>
        <div class="w-100 flex justify-start items-center gap-2 flex-wrap">
        <IconField>
            <InputIcon>
                <i class="pi pi-search" />
            </InputIcon>
            <InputText v-model="filters['global'].value" placeholder="Search stock and company" />
        </IconField>


        <MultiSelect
         v-model="selectedColumns"
         :options="columns"
         optionLabel="header"
         @change="updateVisibleColumns"
         display="template"
         label="Show/Hide Columns"
         :showToggleAll="false"
         class="bg-indigo-500"
       >
         <template #value>
           Show/Hide Columns
         </template>
         <template #footer v-if="showReset">

           <Button label="Reset" style="width: 100%;" @click="resetColumns"/>
         </template>
       </MultiSelect>
       <button type="button"  class="rounded-md  px-3 py-2 bg-indigo-500 text-sm font-semibold text-white shadow-sm ring-1 ring-inset ring-gray-300"  @click="exportCSV($event)" ><i class="pi pi-external-link"></i> Export</button>

       

      
     </div>

     </template>
     

   <template #paginatorstart>
         <div style="display: flex; gap: 10px;">
             <Button v-for="size in [10, 50, 100]" :key="size" :label="size" @click="rows = size" :class="{'p-button-primary': rows === size, 'p-button-outlined': rows !== size}" />
         </div>
     </template>
   
  <template #empty> No customers found. </template>
     <Column  v-if="visibleColumns.includes('stockname')" field="stockname" sortable header="Stockname" exportHeader="Product Code">
         <template #body="{ data }">
             {{ data.stockname }}
         </template>
         <template  #filter="{ filterModel }">
             <InputText v-model="filterModel.value" type="text" placeholder="Search by Stock name" />
         </template>
     </Column>
     <Column 
         v-if="visibleColumns.includes('quantity')" 
         field="quantity" 
         sortable 
         header="Quantity" 
         :showFilterOperator="false" 
         :showFilterMatchModes="false"
     >
     <template #body="{ data }">
       {{ data.quantity }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
     </Column>
     <Column v-if="visibleColumns.includes('avgprice')" field="avgprice" sortable header="Avgprice" :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
       {{ data.avgprice }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4" :min="1" :max="1000"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
     </Column>
     <Column  v-if="visibleColumns.includes('ltp')" field="ltp" sortable header="LTP" :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
       {{ data.ltp }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4" :min="1" :max="1000"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
     </Column>
     <Column v-if="visibleColumns.includes('invamt')" field="invamt" sortable header="Invamt" :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
       {{ data.invamt }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4" :min="1" :max="1000"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
         
     </Column>
     <Column v-if="visibleColumns.includes('mktval')" field="mktval" sortable header="Mktval" :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
       {{ data.mktval }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4" :min="1" :max="100000"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
     </Column>
     <Column v-if="visibleColumns.includes('overall')" field="overall" sortable header="Overall" :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
       {{ data.overall }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4" :min="1" :max="1000"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
     </Column>
     <Column v-if="visibleColumns.includes('days')" field="days" sortable header="Days" :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
       {{ data.days }}
             </template>
             <template #filter="{ filterModel }">
                 <Slider v-model="filterModel.value" range class="m-4" :min="1" :max="1000"></Slider>
                 <div class="flex items-center justify-between px-2">
                     <span>{{ filterModel.value ? filterModel.value[0] : 0 }}</span>
                     <span>{{ filterModel.value ? filterModel.value[1] : 100 }}</span>
                 </div>
             </template>
     </Column>
     <Column v-if="visibleColumns.includes('date')" field="date" header="Date" sortable :showFilterOperator="false" :showFilterMatchModes="false">
       <template #body="{ data }">
             {{ data.date }}
         </template>
         <template  #filter="{ filterModel }">
           <DatePicker 
v-model="filters.date.constraints[0].value" 
dateFormat="yy-mm-dd" 
showIcon
@update:modelValue="applyDateFilter"
/>
         </template>

     </Column>

     
     <Column   v-if="visibleColumns.includes('action')"  field="action" header="Action" :showFilterOperator="false" :showFilterMatchModes="false">
         <template #body="{ data }">
           <button type="button"  @click="rightcanva(data)" class="rounded-md w-full  px-1 py-1 text-sm bg-indigo-500 font-semibold text-white shadow-sm ring-1 ring-inset ring-gray-300" ><i class="pi pi-eye"></i></button>

           
         </template>
        
    </Column>

   </DataTable>

   

 <Drawer v-model:visible="visibleRight" header="Stock Details" position="right" class="!w-90 md:!w-80 lg:!w-[80rem] wd" >


   <hr>
   <div class="w-full p-1 flex flex-col h-full justify-between" >
     <div class="w-full flex wrap" style="border: 1px solid black;">
       <div class="w-2/3 p-1 b-1" style="border: 2px solid blue;" >
         <Tabs value="0">
       <TabList >
           <Tab value="0"><i class="pi pi-asterisk"></i> Activity</Tab>
           <Tab value="1"><i class="pi pi-envelope"></i> Emails</Tab>
           <Tab value="2"><i class="pi pi-comment"></i> Comments</Tab>
           <Tab value="3"><i class="pi pi-database"></i> Data</Tab>
           <Tab value="4"><i class="pi pi-list-check"></i> Tasks</Tab>
           <Tab value="5"><i class="pi pi-clipboard"></i> Notes</Tab>
           <Tab value="6"><i class="pi pi-paperclip"></i> Attachments</Tab>
       </TabList>
       <TabPanels>
       <TabPanel value="0">
           Tab-0
       </TabPanel>
       <TabPanel value="1">
         Tab-1
       </TabPanel>
       <TabPanel value="2">
           Tab-2
       </TabPanel>
       <TabPanel value="3">
         Tab-3
       </TabPanel>
       <TabPanel value="4">
           Tab-4
       </TabPanel>
       <TabPanel value="5">
         Tab-5
       </TabPanel>
       <TabPanel value="6">
         Tab-6
       </TabPanel>
</TabPanels>
</Tabs>


       </div>
       <div class="w-1/3 p-1 b-1" style="border-left: 1px solid gray;">
         <p class="text-black-500 text-xl p-2 mt-3"><b>CRM-123H43</b></p>
         <hr>

         <div class="w-full flex justify-center items-center gap-3 p-2">
           <div class="rounded-full bg-slate-500 w-10 h-10"></div>
           <h1>{{ stockname }}</h1>
         </div>
         <hr>
         <div class="w-full mt-2">
           
         <Accordion value="0">
     <AccordionPanel value="0">
         <AccordionHeader>Details</AccordionHeader>
         <AccordionContent>

           <div class="w-full  flex">
             <div class="w-full " ><span>Stock Name</span></div>
             <div class="w-full " ><span>{{stockname}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>Date</span></div>
             <div class="w-full " ><span>{{dateval}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>Quantity</span></div>
             <div class="w-full " ><span>{{quant}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>AVG Price</span></div>
             <div class="w-full " ><span>{{avg}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>LTP</span></div>
             <div class="w-full " ><span>{{ltp}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>INV Amount</span></div>
             <div class="w-full " ><span>{{invamt}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>MKT Value</span></div>
             <div class="w-full " ><span>{{mktval}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>Over All</span></div>
             <div class="w-full " ><span>{{overall}}</span></div>
           </div>
           <div class="w-full  flex">
             <div class="w-full " ><span>Days</span></div>
             <div class="w-full " ><span>{{days}}</span></div>
           </div>
          
            
         </AccordionContent>
     </AccordionPanel>
     </Accordion>
         </div>
       </div>

     </div>


     
  <div class="w-full p-1 flex justify-center gap-2" >
     <Button label="Proceed" severity="success" @click="proceedfun" raised />
     <Button label="Cancel" severity="danger" @click="cancelfun" variant="outlined" />
 </div> 
   </div>
 </Drawer>
 </div>
</div>
</div>
</div>
</template>

<script setup>
import { ref, computed, onMounted, watch  } from 'vue';
import { FilterMatchMode, FilterOperator } from '@primevue/core/api';
import Slider from 'primevue/slider';
import DatePicker from 'primevue/datepicker';
import 'primeicons/primeicons.css';
import { useToast } from "primevue/usetoast";


import Tabs from 'primevue/tabs';
import TabList from 'primevue/tablist';
import Tab from 'primevue/tab';
import TabPanels from 'primevue/tabpanels';
import TabPanel from 'primevue/tabpanel';


import Accordion from 'primevue/accordion';
import AccordionPanel from 'primevue/accordionpanel';
import AccordionHeader from 'primevue/accordionheader';
import AccordionContent from 'primevue/accordioncontent';

const customfilterbox = ref(false);
const customBox = ref(null);

const todaydate=ref('')
const startdaydate=ref('')
const loading=ref(true)
const content=ref(false)

const investamount=ref('')
const currentvalue=ref('')
const overallgain=ref('')
const todaygain=ref('')

const visibleRight = ref(false);
const rows = ref(10);
const dates = ref([]);
const customers = ref([]);
const activeFilter = ref('week');


const toast = useToast();


const filters = ref();

const myval=ref('')

const customtoggle = () => {

  customfilterbox.value = !customfilterbox.value;
};




const initFilters = () => {
filters.value = {
 global: { value: null, matchMode: FilterMatchMode.CONTAINS },
 stockname: { operator: FilterOperator.AND, constraints: [{ value: null, matchMode: FilterMatchMode.STARTS_WITH }] },
 quantity: { value: [0, 100], matchMode: FilterMatchMode.BETWEEN },
 avgprice: { value: [0, 1000], matchMode: FilterMatchMode.BETWEEN },
 ltp: { value: [0, 1000], matchMode: FilterMatchMode.BETWEEN },
 invamt: { value: [0, 1000], matchMode: FilterMatchMode.BETWEEN },
  mktval: { value: [0, 100000], matchMode: FilterMatchMode.BETWEEN },
  overall: { value: [0, 1000], matchMode: FilterMatchMode.BETWEEN },
  days: { value: [0, 1000], matchMode: FilterMatchMode.BETWEEN },
  date: { operator: FilterOperator.AND, constraints: [{ value: null, matchMode: FilterMatchMode.EQUALS }] },



};
};



const applyDateFilter = () => {
if (filters.value.date.constraints[0].value) {
let selectedDate = filters.value.date.constraints[0].value;
filters.value.date.constraints[0].value = formatDate(selectedDate);
}
};

const formatDate = (date) => {
if (!date) return null;
const d = new Date(date);
return `${d.getFullYear()}-${String(d.getMonth() + 1).padStart(2, "0")}-${String(d.getDate()).padStart(2, "0")}`;
};



initFilters();






const getdata = async () => {
try {
const res = await fetch('/sharetable.json');
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
customers.value = await res.json();
} catch (error) {
console.error("Error:", error.message);
}
};

onMounted(() => {
setInterval(() => {
loading.value=false
content.value=true
}, 500);

filterLastWeek();
getdata();
});

const filterLastWeek = async() => {
activeFilter.value = 'week';
customfilterbox.value=false

try {

const res = await fetch('/amounttable.json');
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
const data = await res.json();
investamount.value=data[0].week.investamount
currentvalue.value=data[0].week.currentvalue
overallgain.value=data[0].week.overallgain
todaygain.value=data[0].week.todaygain

} catch (error) {
console.error("Error:", error.message);
}



setDateRange(6);

};

const filterLast15Days = async() => {

activeFilter.value = '15days';
customfilterbox.value=false
try {

const res = await fetch('/amounttable.json');
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
const data = await res.json();
investamount.value=data[1].day_15.investamount
currentvalue.value=data[1].day_15.currentvalue
overallgain.value=data[1].day_15.overallgain
todaygain.value=data[1].day_15.todaygain

} catch (error) {
console.error("Error:", error.message);
}

setDateRange(14);
};

const filterLastMonth = async() => {
activeFilter.value = 'month';
customfilterbox.value=false
try {

const res = await fetch('/amounttable.json');
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
const data = await res.json();
investamount.value=data[2].month.investamount
currentvalue.value=data[2].month.currentvalue
overallgain.value=data[2].month.overallgain
todaygain.value=data[2].month.todaygain

} catch (error) {
console.error("Error:", error.message);
}
setDateRange(30);
};

const filterLast3Months = async() => {
activeFilter.value = '3months';
customfilterbox.value=false
try {

const res = await fetch('/amounttable.json');
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
const data = await res.json();
investamount.value=data[3].month_3.investamount
currentvalue.value=data[3].month_3.currentvalue
overallgain.value=data[3].month_3.overallgain
todaygain.value=data[3].month_3.todaygain

} catch (error) {
console.error("Error:", error.message);
}
setDateRange(90);
};

const setDateRange = (days) => {
const today = new Date();
const startDate = new Date();
startDate.setDate(today.getDate() - days);
dates.value = [startDate.toISOString().split('T')[0], today.toISOString().split('T')[0]];
myval.value=dates.value





const formatDate = (date) => {
        const options = { day: '2-digit', month: 'short', year: 'numeric', weekday: 'long' };
        return date.toLocaleDateString('en-GB', options)
            .replace(',', '')  // Remove the comma
            .replace(/(\d{2}) (\w{3}) (\d{4}) (\w+)/, '$1-$2-$3 ($4)');
    };

    const formattedToday = formatDate(today);
    const formattedStartDate = formatDate(startDate);

    todaydate.value=formattedToday
    startdaydate.value=formattedStartDate
    

};

const handleDateChange = (newDates) => {
 
activeFilter.value = 'customs';
dates.value = newDates;

console.log(dates.value)
};

console.log(dates.value,"henqweoh")
const filteredCustomers = computed(() => {
 
if (!dates.value || dates.value.length !== 2) {

return customers.value;
}

const startDate = new Date(dates.value[0]);
const endDate = new Date(dates.value[1]);
endDate.setHours(23, 59, 59, 999);

return customers.value.filter(customer => {
const customerDate = new Date(customer.date);
return customerDate >= startDate && customerDate <= endDate;

});

});

const columns = ref([
{ field: 'stockname', header: 'Stockname' },
{ field: 'quantity', header: 'Quantity' },
{ field: 'avgprice', header: 'Avgprice' },
{ field: 'ltp', header: 'Ltp' },
{ field: 'invamt', header: 'Invamt' },
{ field: 'mktval', header: 'Mktval' },
{ field: 'overall', header: 'Overall' },
{ field: 'days', header: 'Days' },
{ field: 'date', header: 'Date' },
{ field: 'action', header: 'Action' },
]);

// Initially select all columns except 'ltp', 'mktval', and 'date'
const selectedColumns = ref(columns.value.filter(col => !['ltp', 'mktval', 'date'].includes(col.field)));
const visibleColumns = ref(selectedColumns.value.map(col => col.field)); // Tracks visibility
const showReset = ref(true); // Ensure reset is visible as some columns are unchecked initially

const updateVisibleColumns = () => {
visibleColumns.value = selectedColumns.value.map(col => col.field);
showReset.value = selectedColumns.value.length < columns.value.length; // Show Reset only when some columns are unchecked
};

const resetColumns = () => {
selectedColumns.value = columns.value.slice(); // Reset to all columns selected
updateVisibleColumns(); // Ensure UI updates
};

watch(selectedColumns, updateVisibleColumns, { deep: true });


const dt = ref();

const exportCSV = () => {
dt.value.exportCSV();
};
const stockname=ref('')
const dateval=ref('')
const quant=ref('')
const avg=ref('')
const ltp=ref('')
const invamt=ref('')
const mktval=ref('')
const overall=ref('')
const days=ref('')

const rightcanva =(dataval)=>{
visibleRight.value=true
stockname.value=dataval.stockname
dateval.value=dataval.date
quant.value=dataval.quantity
avg.value=dataval.avgprice
ltp.value=dataval.ltp
invamt.value=dataval.invamt
mktval.value=dataval.mktval
overall.value=dataval.overall
days.value=dataval.days
}

const proceedfun=async()=>{
const formdata=new FormData()
formdata.append('stockname', stockname.value)
formdata.append('date', dateval.value)
formdata.append('quantity', quant.value)
formdata.append('averageprice', avg.value)
formdata.append('ltp', ltp.value)
formdata.append('invamt', invamt.value)
formdata.append('mktval', mktval.value)
formdata.append('overall', overall.value)
formdata.append('days', days.value)
const api='https://fakestoreapi.com/products'
try {
const res = await fetch(api,{
 method:'POST',
 body:formdata
});
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
const data = await res.json();
toast.add({ severity: 'success', summary: 'Success Message', detail: data.id, life: 3000 });
} catch (error) {
console.error("Error:", error.message);
}


}

const cancelfun=async()=>{
const formdata=new FormData()
formdata.append('stockname', stockname.value)
formdata.append('date', dateval.value)
formdata.append('quantity', quant.value)
formdata.append('averageprice', avg.value)
formdata.append('ltp', ltp.value)
formdata.append('invamt', invamt.value)
formdata.append('mktval', mktval.value)
formdata.append('overall', overall.value)
formdata.append('days', days.value)
const api='https://fakestoreapi.com/products'
try {
const res = await fetch(api,{
 method:'POST',
 body:formdata
});
if (!res.ok) throw new Error(`HTTP error! Status: ${res.status}`);
const data = await res.json();
toast.add({ severity: 'error', summary: 'Cancel Message', detail: data.id, life: 3000 });
} catch (error) {
console.error("Error:", error.message);
}
}
</script>
<style>

@media(max-width:992px){
.mylist{
width: 100% !important;
}
.wd{
width: 100% !important;
}

.wrap{
flex-direction: column !important;
}
.b-1{
width: 100% !important;
}
}
</style>