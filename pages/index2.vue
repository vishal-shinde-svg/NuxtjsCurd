<template>
<div>
    <form @submit="btnSubmit" class="bg-gray-100 border-black rounded-lg border-2 px-12">

        <div>

            <table class="list">

                <tr>
                    <!-- <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">id</th> -->

                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">First Name</th>

                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">Last Name</th>

                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">Company</th>

                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">Phone number</th>

                    <!-- <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">web_site</th> -->
                    <!-- <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">unique vishitors</th> -->
                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">Email Address</th>
                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">password</th>
                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">confirm passord</th>
                    <th class="text-sm font-medium text-gray-900 px-6 py-4 text-left">Action</th>

                </tr>

                <tr v-for="(item ) in users" :key="item">

                    <!-- <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.Id}}</td> -->

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.firstname}}</td>

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.lastname}}</td>

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.company}}</td>

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.phonenumber}}</td>

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.email}}</td>

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.password}}</td>

                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{{item.confirmpassword}}</td>
                    <button class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20" @click="userDelete(index)">
                        Delete
                    </button>
                    <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20" @click="onEdit(index)">
                        Edit
                    </button>

                    <!-- <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"> -->

                    <!-- <div v-if="Editmode">

                            <a v-on:click="OnEdit(item.Id)" href="#">Edit</a>

                            <a v-on:click="OnDelete(item.Id)" href="#">Delete</a>

                        </div>

                        <div v-if="updatemode"><a href="#">update</a> <a href="#">Cancel</a> </div>

                    </td>  -->

                </tr>

            </table>

            <br />

            <div class="grid gap-6 mb-6 md:grid-cols-2">
                <!-- <div>
                    <label for="id" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">id</label>
                    <input type="text" id="id" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.id" placeholder="Ener id" required>
                </div> -->
                <div>
                    <label for="first_name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">First name</label>
                    <input type="text" id="first_name" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.firstname" required>
                </div>
                <div>
                    <label for="last_name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Last name</label>
                    <input type="text" id="last_name" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.lastname" required>
                </div>
                <div>
                    <label for="company" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Company</label>
                    <input type="text" id="company" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.company" required>
                </div>
                <div>
                    <label for="phone" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Phone number</label>
                    <input type="tel" id="phone" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.phonenumber" required>
                </div>
                <!-- <div>
                    <label for="website" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Website URL</label>
                    <input type="url" id="website" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="flowbite.com" required>
                </div>
                <div>
                    <label for="visitors" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Unique visitors (per month)</label>
                    <input type="number" id="visitors" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="" required>
                </div> -->
            </div>
            <div class="mb-6">
                <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Email address</label>
                <input type="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.email" required>
            </div>
            <div class="mb-6">
                <label for="password" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Password</label>
                <input type="password" id="password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.password" required>
            </div>
            <div class="mb-6">
                <label for="confirm_password" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Confirm password</label>
                <input type="password" id="confirm_password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.confirmpassword" required>
            </div>
            <div class="flex items-start mb-6">
                <div class="flex items-center h-5">
                    <input id="remember" type="checkbox" value="" class="w-4 h-4 bg-gray-50 rounded border border-gray-300 focus:ring-3 focus:ring-blue-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-600 dark:ring-offset-gray-800" required>
                </div>
                <label for="remember" class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-400">I agree with the <a href="#" class="text-blue-600 hover:underline dark:text-blue-500">terms and conditions</a>.</label>
            </div>

            <!-- <button type="button" class="mx-3" v-on:click="btnSubmit()">{{btnMode}} </button> -->
            <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800" @click="btnSubmit">Submit</button>
            <button type="reset" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Reset</button>
        </div>

    </form>
</div>
</template>

<script>
export default {
    data() {
        return {
            isEdit: false,
            indexEdit: -1,
            users: [],
            user: {
                // id: '',
                firstname: '',
                lastname: '',
                company: '',
                phonenumber: '',
                email: '',
                 password: '',
                confirmpassword: '',
            },

        };
    },
    methods: {
            btnSubmit(event) {
            event.preventDefault();
            if (this.isEdit == true) {
                this.users[this.indexEdit] = this.user;
                this.isEdit = false;
                this.indexEdit = -1;
            } else {
                this.users.push(this.user);
            }
            this.user = {
                firstname: '',
                lastname: '',
                company: '',
                phonenumver: '',
                email: '',
                password: '',
                confirmpassword: ''
            };
            console.log(this.users)

        },
        // onReset(event) {
        //     event.preventDefault();
        //     this.form.email = "";
        //     this.form.name = "";
        //     this.form.address = "";
        //     this.form.contact = "";
        //     this.form.city=""
        // },
        userDelete(index) {
            this.users.splice(index, 1)
        },
        onEdit(index) {
            this.user.firstname = this.users[index].firstname;
            this.user.lastname = this.users[index].lastname;
            this.user.company = this.users[index].company;
            this.user.phonenumber = this.users[index].phonenumber;
            this.user.email = this.users[index].email;
            this.user.password = this.users[index].password;
            this.user.confirmpassword = this.users[index].confirmpassword;
            this.isEdit = true;
            this.indexEdit = index;
        }
    }
}
</script>

<style>

</style>
