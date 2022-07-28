<template>
<main class="flex justify-center w-full h-screen">
    <div>
        <form @submit="formSubmit" class="bg-gray-100 border-black rounded-lg border-2 px-12">
            <table>
                <h2 class="text-teal-900 text-xl font-bold pt-6">Information Form</h2>
                <hr />
                <br />
                <label class="pt-10 py-10 " for="firstname">First name:</label><br />
                <input type="text" v-model="user.firstname" id="firstname" name="firstname" placeholder="Enter your first name" /><br /><br />
                <label for="lastname">Last name:</label><br />
                <input type="text" v-model="user.lastname" id="lastname" name="lastname" placeholder="Enter your Last name" /><br /><br />
                <label for="address"> address: </label><br />
                <input type="text" v-model="user.address" id="address" name="address" placeholder="Enter your address" />
                <br /><br />
                <label for="number">Phone Number: </label><br />
                <input type="number" v-model="user.number" id="number" name="number" placeholder="Enter your number" />
                <br /><br />
                <div>
                    <button class="py-1 px-5 mr-5 bg-blue-500 hover:bg-blue-700 text-white font-bold text-center rounded-md mb-3" type="submit" @click="formSubmit"> Submit </button>
                    <button class="py-1 px-5 bg-blue-500 hover:bg-blue-700 text-white font-bold text-center rounded-md mb-3" type="reset"> Reset </button>
                </div>
            </table>
        </form>
        <br>
        <table class="list">
            <tr>
                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-4 border-black rounded-lg border-2">First Name</th>
                <th class="px-4 border-black rounded-lg border-2">Last Name</th>
                <th class="px-4 border-black rounded-lg border-2">Address</th>
                <th class="px-4 border-black rounded-lg border-2">Contact No</th>
                <th class="px-4 border-black rounded-lg border-2">Action</th>
            </tr>
            <tr v-for="(item,index) in users" v-bind:index="index" :key="item">
            <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-4 border-black rounded-lg border-2">{{item.firstname}}</td>
                <td class="px-4 border-black rounded-lg border-2">{{item.lastname}}</td>
                <td class="px-4 border-black rounded-lg border-2">{{item.address}}</td>
                <td class="px-4 border-black rounded-lg border-2">{{item.number}}</td>
                <td class="px-4 border-black rounded-lg border-2">{{item.Action}}

                    <button class="mx-3" @click="userDelete(index)">
                        Delete
                    </button >
                     <!-- <button class="mx-3" @click="onDelete(item.id)">
                        Edit
                    </button> -->

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
            users: [],
            user: {
                firstname: '',
                lastname: '',
                address: '',
                number: '',
            },
        };
    },
    methods: {
        formSubmit(event) {
            event.preventDefault();
            this.users.push(this.user);
            this.user = {
                firstname: '',
                lastname: '',
                address: '',
                number: ''
            };
        }
        ,
        onReset(event) {
      event.preventDefault();
    this.form.email = "";
      this.form.name = "";
      this.form.address = "";
      this.form.contact = "";
     
    },
    userDelete(index){
       this.users.splice(index,1)  
            

    }
  }
}


</script>
