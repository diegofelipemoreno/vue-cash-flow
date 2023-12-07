<template>
  <Layout>
    <template #header>
        <Header></Header>
    </template>
    <template #resume>
        <Resume
            :total-label="'Total Saving'"
            :label="'Total Saving'"
            :amount="amount"
            :totalAmount="'900000'"
            @showModal="showModal"
        >
            <template #graphic>
                <Graphic />
            </template>
        </Resume>
    </template>
    <template #movements>
      <Movements 
      :movements="movements" />
    </template>
  </Layout>

          <div class="body" v-show="isModalShown">
            <h1>ISI</h1>
        </div>
  
  <Modal v-show="isModalShown">
    <template #modalContent>
        <Form/>
    </template>
  </Modal>
  
</template>

<script>
    import Layout from '@/components/Layout.vue';
    import Header from '@/components/Header.vue';
    import Resume from '@/views/Resume.vue';
    import Movements from '@/views/Movements.vue';
    import Graphic from '@/components/Graphic.vue';
    import Modal from '@/components/Modal.vue';
    import Action from '@/components/Action.vue';
    import Form from '@/components/Form.vue';

    export default {
        components: {
            Layout,
            Header,
            Resume,
            Movements,
            Graphic,
            Action,
            Modal,
            Form
        },
        methods: {
            showModal() {
                this.isModalShown = !this.isModalShown;
            }
        },
        data() {
            return {
                isModalShown: false,
                label: null,
                amount: null,
                movements: [
                    {
                        id: 0,
                        title: "Movement 0",
                        description: "Movement 0 description",
                        amount: 10000

                    },
                                        {
                        id: 1,
                        title: "Movement 1",
                        description: "Movement 1 description",
                        amount: 10000

                    },
                                        {
                        id: 2,
                        title: "Movement 2",
                        description: "Movement 2 description",
                        amount: 10000

                    },
                                        {
                        id: 3,
                        title: "Movement 3",
                        description: "Movement 3 description",
                        amount: 10000

                    },
                                        {
                        id: 4,
                        title: "Movement 4",
                        description: "Movement 14 description",
                        amount: 10000

                    },
                                        {
                        id: 5,
                        title: "Movement 5",
                        description: "Movement 1 description",
                        amount: 10000

                    }
                ],
            }
        }
    };
</script>

<style></style>
