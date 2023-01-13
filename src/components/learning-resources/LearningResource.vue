<template>
    <li>
        <base-card>
            <header>
                <h3>{{ title }}</h3>
                    <base-button @click="deleteResource(id)" mode="flat">Delete</base-button>
            </header>
            <p>{{ description }}</p>
            <nav>
                <a :href="link">View Resource</a>
            </nav>
        </base-card>
    </li>
</template>

<script>

export default {

    props: [
        "id",
        "title",
        "description",
        "link"
    ],
    inject: [
        "deleteResource"
    ]
}

</script>

<style scoped>
    li {
        list-style: none;
    }

    header {
        display: flex;
        justify-content: space-between;
    }

    a {
        color: gold;
        text-decoration: none;
        font-size: 1.2rem;
    }
</style>