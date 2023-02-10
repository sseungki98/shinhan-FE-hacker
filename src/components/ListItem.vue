<template>
    <ol class="list">
        <li v-for="item in listData" v-bind:key="item.id" class="list">
            <b>{{ item.time_ago }}</b>
            <template v-if="$route.name === 'news'">
                <span>
                    by <router-link :to="`/user/${item.user}`"> {{ item.user }} </router-link></span
                ><br />
                <a v-bind:href="item.url">{{ item.title }}</a>
                <router-link :to="`item?id=${item.id}`"
                    ><i>({{ item.comments_count }})</i></router-link
                >
            </template>
            <template v-else-if="$route.name === 'ask'">
                <span> by {{ item.user }}</span
                ><br />
                <router-link :to="item.url"
                    >{{ item.title }}<i>({{ item.comments_count }})</i></router-link
                >
            </template>
            <template v-else>
                <span> by {{ item.user }}</span
                ><br />
                <a v-bind:href="item.url"
                    >{{ item.title }}<i>({{ item.comments_count }})</i></a
                >
            </template>
        </li>
    </ol>
</template>

<script>
export default {
    props: ["listData"],
};
</script>

<style></style>
