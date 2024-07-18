<template>
    <v-list>
        <v-list-item :prepend-avatar="props.user.avatar" :subtitle="props.user.email"
            :title="props.user.first_name">
        </v-list-item>
    </v-list>

    <v-divider></v-divider>

    <v-list :lines="false" density="compact" nav>
        <RouterLink v-for="(item, i) in items" :key="i" :to="item.to">
            <v-list-item :value="item" color="primary">
                <template v-slot:prepend>
                    <v-icon :icon="item.icon"></v-icon>
                </template>

                <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item>
        </RouterLink>

    </v-list>
</template>
<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    user: Object
})

const items = [
    { text: 'My Files', icon: 'mdi-folder', to: '/Form' },
    { text: 'Shared with me', icon: 'mdi-account-multiple', to: '/' },
]
</script>