<template>
<main class="flex justify-center w-full h-screen">
    <div>
        <form @submit="formSubmit" class="bg-gray-100 border-blue-400 rounded-lg border-2 px-12">
            <table>
                <h2 class="text-teal-900 text-xl font-bold pt-6">Information Form</h2>
                <hr />
                <br />
                <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300" for="firstname">First name:</label>
                <input type="text" id="firstname" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.firstname" required>
                <label for="lastname" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Last name:</label>
                <input type="text" id="lastname" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.lastname" required>
                <label for="company" class="block  text-sm font-medium text-gray-900 dark:text-gray-300"> company: </label>
                <input type="text" id="company" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.company" required>

                <label for="select" class="block  text-sm font-medium text-gray-900 dark:text-gray-300"> Select Role: </label>
                 <select class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"  v-model="user.role">

                    <option value="Select">Select</option>

                    <option value="Admin">Admin</option>

                    <option value="Member">Member</option>

                </select>


                
                <label for="number" class="block  text-sm font-medium text-gray-900 dark:text-gray-300">phonenumber: </label>
                <input type="text" id="phonenumber" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.phonenumber" required>
                
                <label for="text" class="block text-sm font-medium text-gray-900 dark:text-gray-300">email </label>
                <input type="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.email" required>

                <label for="text" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">password </label>
                <input type="password" id="password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.password" required>

                <label for="text" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">confirm password</label>
                <input type="text" id="confirmpassword" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.confirmpassword" required>
                <br /><br />
                <div>
                    <button  id="btnsubmit" class="py-1 px-5 mr-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3" type="submit" @click="formSubmit" > Submit </button>
                    <button class="py-1 px-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3" type="reset"> Reset </button>
                </div>
            </table>
        </form>
        <br>
        
        <input type="search" class="form-control relative flex-auto min-w-0 block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none" placeholder="Search" v-model="search" aria-label="Search"  aria-describedby="button-addon3"> <br>
        <div v-for="s in searchData" :key="s"></div>
        <p>{{this.s}}</p>
      <button class="btn inline-block px-6 py-2 border-2 border-blue-600 text-blue-600 font-medium text-xs leading-tight uppercase rounded hover:bg-black hover:bg-opacity-5 focus:outline-none focus:ring-0 transition duration-150 ease-in-out" type="button" id="button-addon3"  @click="onsearchData">Search</button>
       
     <!-- <input type="text" id="myInput" @click="myFunction" placeholder="Search for names.." title="Type in a name"> -->
        <br>
        <br>
        <table class="list" id="list">
            
            <tr>
                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-4 border-blue-400 rounded-lg border-4">First Name</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Last Name</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">company</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">role</th>

                <th class="px-4 border-blue-400 rounded-lg border-4">phonenumber</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">email</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">password</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">confirmpassword</th>
            </tr>
            <tr v-for="(item,index) in users" v-bind:index="index" :key="item">
                <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.firstname}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.lastname}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.company}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.role}}</td>

                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.phonenumber}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.email}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.password}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.confirmpassword}}
                    <button class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20" @click="userDelete(index)">
                        Delete
                    </button>
                    <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20" @click="onEdit(index)">
                        Edit
                    </button>
                </td>
            </tr>
        </table>
    </div>
</main>
</template>

<script>
export default {
    data() {
        return {
            search : '',
            isEdit: false,
            indexEdit: -1,
            users: [],
            user: {
                firstname: '',
                lastname: '',
                company: '',
                role:'Select',
                phonenumber: '',
                email: '',
                password: '',
                confirmpassword: ''
            },
        };
    },
    methods: {
        formSubmit(event) {
            event.preventDefault();
            if (this.isEdit == true) {
                this.users[this.indexEdit] = this.user;
                this.isEdit = false;
                this.indexEdit = -1;
                 confirm(' data Successfully Updated');
            } else {
                this.users.push(this.user);
                confirm('Data is successfully added');
            }
            this.user = {
                firstname: '',
                lastname: '',
                company: '',
                role:'Select',
                phonenumber: '',
                email: '',
                password: '',
                confirmpassword: '',
            };
        },
        // onReset(event) {
        //     event.preventDefault();
        //     this.form.email = "";
        //     this.form.name = "";
        //     this.form.address = "";
        //     this.form.contact = "";
        //     this.form.city=""
        userDelete(index) {
            if(confirm('you want to delet data ?')){
            this.users.splice(index, 1)
            }
        },
        onEdit(index) {
            document.getElementById("btnsubmit").innerHTML='Update'
            this.user.firstname = this.users[index].firstname;
            this.user.lastname = this.users[index].lastname;
            this.user.company = this.users[index].company;
            this.user.company = this.usrs[index].company;
            this.user.phonenumber = this.users[index].phonenumber;
            this.user.email = this.users[index].email;
            this.user.password = this.users[index].password;
            this.user.confirmpassword = this.users[index].confirmpassword;
            this.isEdit = true;
            this.indexEdit = index;
        },
        //  myFunction() {
        //     var input, filter, table, tr, td, i, txtValue;
        //     input = document.getElementById("myInput");
        //     filter = input.value.toUpperCase();
        //     table = document.getElementById("list");
        //     tr = table.getElementsByTagName("tr");
        //     for (i = 0; i < tr.length; i++) {
        //         td = tr[i].getElementsByTagName("td")[0];
        //         if (td) {
        //             txtValue = td.textContent || td.innerText;
        //             if (txtValue.toUpperCase().indexOf(filter) > -1) {
        //                 tr[i].style.display = "";
        //             } else {
        //                 tr[i].style.display = "none";
        //             }
        //         }
        //     }
        //  },
    searchData(){
        return this.users.filter(s => s.firstname.includes(this.search) )
    },
    }
}
</script>