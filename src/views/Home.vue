<template>
  <div>
    <h1>Create an event</h1>
    <form @submit.prevent="onSubmit">
      <BaseSelect
        v-model="eventData.category"
        label="Select a category"
        :options="categories"
      />

      <h3>Name & describe your event</h3>
      <BaseInput v-model="eventData.title" label="Title" />

      <BaseInput v-model="eventData.description" label="Description" />

      <h3>Where is your event?</h3>

      <BaseInput v-model="eventData.location" label="Location" />

      <h3>Are pets allowed?</h3>

      <BaseRadioGroup
        :optionsValue="optionsValue"
        v-model="eventData.pets"
        name="pets"
      />

      <h3>Extras</h3>
      <BaseCheckbox label="Catering" v-model="eventData.extras.catering" />
      <BaseCheckbox label="Live music" v-model="eventData.extras.music" />

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      optionsValue: [
        { label: "Yes", value: 1 },
        { label: "No", value: 0 },
      ],
      categories: [
        "sustainability",
        "nature",
        "animal welfare",
        "housing",
        "education",
        "food",
        "community",
      ],
      eventData: {
        category: "",
        title: "",
        description: "",
        location: "",
        pets: 1,
        extras: {
          catering: false,
          music: false,
        },
      },
    };
  },
  methods: {
    async onSubmit() {
      try {
        const res = await axios.post(
          "https://my-json-server.typicode.com/AlexNeo68/vue-3-form/events",
          this.eventData
        );
        console.log(res);
      } catch (error) {}
    },
  },
};
</script>
