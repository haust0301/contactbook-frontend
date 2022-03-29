<script>
export default {
    props: {
        contacts: { type: Array, default: [] },
        activeIndex: { type: Number, default: -1 },
    },
    emits: ["update:activeIndex"],
    computed: {
        selectedIndex() {
            return this.activeIndex;
        },
    },
    methods: {
        select(index) {
            this.$emit("update:activeIndex", index);
        },
    },
};
</script>

<template>
    <ul class="list-group">
        <li
            class="list-group-item"
            v-for="(contact, index) in contacts"
            :key="contact.id"
            :class="{ active: index === selectedIndex }"
            @click="select(index)"
        >
            {{ contact.name }}
        </li>
    </ul>
</template>