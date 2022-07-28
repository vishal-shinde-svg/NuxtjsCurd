<template>
  <div class="grid place-items-center">
    <button type="button"
class="  bg-orange-400 my-4 border required:border-red-500 rounded hover:rounded-lg" @click="addClick()">
 Add Employee
</button>

<table class="min-w-full text-center">
<thead class="border-b">
    <tr>
        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4">
            Employee Id
        </th>
        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4">
            Employee Name
        </th>
        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4">
            Department
        </th >
        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4">
            DOJ
        </th>
        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4">
            Options
        </th>
    </tr>
</thead>
<tbody>
    <tr  class="border-b " v-for="emp in employees" :key="emp" >
        <td  class="text-sm text-gray-900 font-medium px-6 py-4 whitespace-nowrap">{{emp.EmployeeId}}</td>
        <td  class="text-sm text-gray-900 font-medium px-6 py-4 whitespace-nowrap ">{{emp.EmployeeName}}</td>
        <td  class="text-sm text-gray-900 font-medium px-6 py-4 whitespace-nowrap">{{emp.Department}}</td>
        <td  class="text-sm text-gray-900 font-medium px-6 py-4 whitespace-nowrap">{{emp.DateOfJoining}}</td>
        <td  class="text-sm text-gray-900 font-medium px-6 py-4 whitespace-nowrap">
            <button type="button"
            class=" bg-orange-400 my-4 border required:border-red-500 rounded hover:rounded-lg" @click="editClick(emp)">
                <!-- <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil-square" viewBox="0 0 16 16">
                <path d="M15.502 1.94a.5.5 0 0 1 0 .706L14.459 3.69l-2-2L13.502.646a.5.5 0 0 1 .707 0l1.293 1.293zm-1.75 2.456-2-2L4.939 9.21a.5.5 0 0 0-.121.196l-.805 2.414a.25.25 0 0 0 .316.316l2.414-.805a.5.5 0 0 0 .196-.12l6.813-6.814z"/>
                <path fill-rule="evenodd" d="M1 13.5A1.5 1.5 0 0 0 2.5 15h11a1.5 1.5 0 0 0 1.5-1.5v-6a.5.5 0 0 0-1 0v6a.5.5 0 0 1-.5.5h-11a.5.5 0 0 1-.5-.5v-11a.5.5 0 0 1 .5-.5H9a.5.5 0 0 0 0-1H2.5A1.5 1.5 0 0 0 1 2.5v11z"/>
                </svg> -->
            </button>
            <button type="button" @click="deleteClick(emp.EmployeeId)"
            class=" bg-orange-400 my-4 border required:border-red-500 rounded hover:rounded-lg">
                <!-- <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash-fill" viewBox="0 0 16 16">
                <path d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1H2.5zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5zM8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5zm3 .5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 1 0z"/>
                </svg> -->
            </button>

        </td>
    </tr>
</tbody>
<!-- </thead> -->
</table>

<div class="" id="exampleModal" >
<div class="">
<div class="modal-content">
    <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">{{modalTitle}}</h5>
        <button type="button" class=" bg-orange-400 my-4 border required:border-red-500 rounded hover:rounded-lg"></button>
    </div>

    <div class="modal-body">
    <div class="">
        <div class="">
            <div class="">
                <span class="input-group-text">Name</span>
                <input type="text" class="form-control" v-model="EmployeeName">
            </div>

            <div class="">
                <span class="input-group-text">Department</span>
                <select class="form-select" v-model="Department">
                    <option v-for="dep in departments" :key="dep">
                    {{dep.DepartmentName}}
                    </option>
                </select>
            </div>

            <div class="">
                <span class="">DOJ</span>
                <input type="date" class="form-control" v-model="DateOfJoining">
            </div>

        </div>
        <!-- <div class="p-2 w-50 bd-highlight">
            <img width="250px" height="250px"
                :src="PhotoPath+PhotoFileName"/>
            <input class="m-2" type="file" @change="imageUpload">
        </div> -->
    </div>
    
        <button type="button" @click="createClick()"
        v-if="EmployeeId==0" class="">
        Create
        </button>
        <button type="button" @click="updateClick()"
        v-if="EmployeeId!=0" class="btn btn-primary">
        Update
        </button>

    </div>

</div>
</div>
</div>


</div>

</template>

<script>
export default {

}
</script>

<style>

</style>