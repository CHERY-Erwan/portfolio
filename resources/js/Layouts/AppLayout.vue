<template>
<v-card>
    <v-layout>
        <v-app-bar title="Application bar"></v-app-bar>

        <v-navigation-drawer
            v-model="drawer"
            :rail="rail"
            permanent
            theme="dark"
            class="bg-deep-purple"
        >
            <v-list-item
                :class="rail ? 'ml-2 mt-2' : 'ml-1 mt-1'"
                prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
                title="John Leider"
                nav
            >
                <template v-slot:append>
                    <v-btn
                        icon="mdi-chevron-left"
                        variant="text"
                        @click.stop="rail = !rail"
                    ></v-btn>
                </template>
            </v-list-item>

            <v-divider></v-divider>

            <v-list density="compact" nav>
                <v-list-item v-if="rail" @click="rail = ! rail" prepend-icon="mdi-chevron-right" title="openNav" value="openNav"></v-list-item>
                <v-list-item prepend-icon="mdi-view-dashboard" title="Dashboard" value="dashboard"></v-list-item>
                <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
                <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
            </v-list>

            <template v-slot:append>
                <div class="pa-2">
                    <v-btn block>
                        <v-icon v-if="rail">mdi-logout</v-icon>
                        <span v-else>{{ $t('logout') }}</span>
                    </v-btn>
                </div>
            </template>
        </v-navigation-drawer>

        <v-main>
            <slot />
        </v-main>
    </v-layout>
</v-card>
</template>

<script setup>
import { ref } from 'vue';

const drawer = ref(null);
const rail = ref(null);
</script>