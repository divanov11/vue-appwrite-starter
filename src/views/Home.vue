<script setup>
import { computed, ref, onMounted } from 'vue'
import {databases} from '../appwrite'
import { useUserStore } from '../store'
import LogoutButton from '../components/LogoutButton.vue'

const store = useUserStore()
const user = computed(() => store.user)

// const loading = ref(false)
// const items = ref([])
// const error = ref(null)

// async function fetchData() {
//   loading.value = true
  
//   try {
//     const response = await databases.listDocuments('prod', 'items')
//     items.value = response.documents
//   } catch (err) {
//     error.value = err.toString()
//   } finally {
//     loading.value = false
//   }
// }

// onMounted(() => {
//     fetchData();
// });

</script>

<template>
    <div  style="display: flex; justify-content: center; align-items: center; flex-direction: column;">
        <h3>Welcome {{user.name ? (user.name) : (user.email)}}! 👋</h3>
    </div>

    <div>
        <div v-if="loading" class="loading">Loading...</div>
        <div v-if="error" class="error">{{ error }}</div>

        <!-- <div>
            <h4>Here is your shopping list 📝</h4>

            <div v-for="item in items" :key="item.$id">
                <input type="checkbox"/>
                {{ item.body }}
            </div>

        </div> -->
    </div>

    <LogoutButton/>
</template>
