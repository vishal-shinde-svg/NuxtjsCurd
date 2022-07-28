<template>
<div class="grid place-items-center">

    <table>

        <tr>
            <td>
                <form action="" class="text-sm m-8 xs:p-4 sm:p-4 md:p-8 lg:p-8 " autocomplete="off" onsubmit="onFormSubmit()">
                    <h1 class="font-bold  text-2xl my-4 rounded justify-between "> User Registration Form </h1>

                    <div class=" rounded mb-4 shadow appearance-none label-floating">
                        <label class=" mx-4 text-bold mb-4 " for="EmpNo">EmpNo</label>
                        <input class="w-full py-2 px-3 text-black leading-normal rounded" type="text" name="EmpNo" id="EmpNo">
                    </div>
                    <div class=" rounded mb-4 shadow appearance-none label-floating">
                        <label class=" mx-4 text-bold mb-4 " for="firstName">FirstName</label>
                        <input class="w-full py-2 px-3 text-black leading-normal rounded" type="text" name="firstName" id="firstName">
                    </div>
                    <div class=" rounded mb-4 shadow appearance-none label-floating">
                        <label class=" mx-4 text-bold mb-4 " for="lastName">LastName</label>
                        <input class="w-full py-2 px-3 text-black leading-normal rounded" type="text" name="lastName" id="lastName">
                    </div>

                    <div class=" rounded mb-4 shadow appearance-none label-floating ">
                        <label class=" mx-4 text-bold mb-8 " for="firstName">Password</label>
                        <input class="w-full py-2 px-3 text-black leading-normal rounded" type="password" name="Password" id="Password">
                    </div>
                    <div class=" rounded mb-4 shadow appearance-none label-floating">
                        <label class=" mx-4 text-bold mb-4 " for="lastName">pwd</label>
                        <input class="w-full py-2 px-3 text-black leading-normal rounded" type="password" name="pwd" id="pwd">
                    </div>

                    <div class="form_action-button flex flex-wrap py-2 items-center justify-evenly pt-4 my-4">
                        <input class="bg-black hover:bg-white hover:text-black text-white py-2 px-4 rounded" type="submit" value="Submit" @click="addClick()">

                        <div class="form_action-button flex flex-wrap py-2 items-center justify-evenly pt-4 my-3" @click="addClick()">
                            <input class="bg-black hover:bg-white hover:text-black text-white  py-2 px-4 rounded" type="reset" value="Reset">
                        </div>
                    </div>
                </form>

            <td>
            </td>
            

            <table class="list table-auto top-12 border-black border-separate border border-slate-400" id="storelist">

                <thead>
                    <tr>
                        <th class="border border-slate-300">EmpNo</th>
                        <th class="border border-slate-300">FirstName</th>
                        <th class="border border-slate-300">LastName</th>
                        <th class="border border-slate-300">Password </th>
                        <th class="border border-slate-300">pwd</th>
                        <th class="border border-slate-300"> Action</th>
                        <!-- <th class="border border-slate-300"> Action <button>Edit</button> <button>DElete</th> -->

                    </tr>
                    <tr v-for="dep in userdetais" :key="dep">
                        <td>{{dep.EmpNo}}</td>
                        <td>{{dep.FirstName}}</td>
                        <td>{{dep.LastName}}</td>
                        <td>{{dep.password}}</td>
                        <td>{{dep.pwd}}</td>
                        <td>
                        </td>
                    </tr>

                </thead>
                <tbody class="border border-slate-300">

                </tbody>
                
            </table>

            </td> 
        </tr>
        
    </table>
</div>
</template>

<script>
export default {
    data() {
        return {
            userdetais: [],
            EmpNo: "",
            FirstName: "",
            LastName: "",
            password: "",
            pwd: "",

        }

    },
    methods:{
        addClick(){
        this.EmpNo="";
        this.FirstName="";
        this.LastName="";
        this.password="";
        this.pwd="";

    },
    
    methods:{
    refreshData(){
        axios.get(variables.API_URL+"employee")
        .then((response)=>{
            this.employees=response.data;
        });

        axios.get(variables.API_URL+"department")
        .then((response)=>{
            this.departments=response.data;
        });
}
    }
    },
    addClick(){
        this.EmpNo="";
        this.FirstName="";
        this.LastName="";
        this.password="";
        this.pwd="";
    },
    editClick(emp){
        this.EmpNo=emp.EmpNp;
        this.FirstName=emp.FirstName;
        this.LastName=emp.LastName;
        this.password=emp.Password;
        this.pwd=emp.Pwd;
    },
    createClick(){
        axios.post(variables.API_URL+"employee",{
            EmployeeName:this.EmployeeName,
            Department:this.Department,
            DateOfJoining:this.DateOfJoining,
            PhotoFileName:this.PhotoFileName
        })
        .then((response)=>{
            this.refreshData();
            alert(response.data);
        });
    },
    updateClick(){
        axios.put(variables.API_URL+"employee",{
            EmployeeId:this.EmployeeId,
            EmployeeName:this.EmployeeName,
            Department:this.Department,
            DateOfJoining:this.DateOfJoining,
            PhotoFileName:this.PhotoFileName
        })
        .then((response)=>{
            this.refreshData();
            alert(response.data);
        });
    },
    deleteClick(id){
        if(!confirm("Are you sure?")){
            return;
        }
        axios.delete(variables.API_URL+"employee/"+id)
        .then((response)=>{
            this.refreshData();
            alert(response.data);
        });

    },
    imageUpload(event){
        let formData=new FormData();
        formData.append('file',event.target.files[0]);
        axios.post(
            variables.API_URL+"employee/savefile",
            formData)
            .then((response)=>{
                this.PhotoFileName=response.data;
            });
    }

}
// mounted:function(){
//     this.refreshData();
// }


    


</script>

<style>

</style>
