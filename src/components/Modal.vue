<template>
    <div class="backdrop" @click.self="closeModal" @mousedown.self="closeModalTwo">
        <div class="modal" :class="{ sale: theme === 'sale'}">
            <slot></slot>
            <div class="actions">
                <slot name="links"></slot>
                <slot name="linksTwo"></slot>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['theme'],
    methods: {
        closeModal() {
            this.$emit('close')
        },
        closeModalTwo() {
            this.$emit('leave')
        }
    }
}
</script>
<style >
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: #dedede;
        border-radius: 7px;
        border: none;
    }
    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }
    .modal h1 {
        color: rgb(87, 87, 87);
        background: #ffe6e6;
    }
    .modal p {
        font-style: normal;
        font-weight: 600;
    }
    .modal.sale {
        color: crimson;
        background: #dedede;
    }
    .modal.sale h1 {
        color: #000000;
    }
    .modal.dark {
        color: #989898;
        background: #000000;
    }
    a {
        margin: 8px 15px;
        padding: 8px 15px;
        text-decoration: none;
        color: #ffffff;
        background: #520606;
        border-radius: 4px;
        justify-content: center;
        align-items: center;
    }
</style>