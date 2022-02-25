<template>
  <div>
    <h1>Create an event</h1>
    <form>
      <BaseSelect
        v-model="event.category"
        label="Select a category"
        :options="categories"
      />

      <h3>Name & describe your event</h3>
      <BaseInput v-model="event.title" label="Title" />

      <BaseInput v-model="event.description" label="Description" />

      <h3>Where is your event?</h3>

      <BaseInput v-model="event.location" label="Location" />

      <h3>Are pets allowed?</h3>

      <BaseRadioGroup
        :optionsValue="optionsValue"
        v-model="event.pets"
        name="pets"
      />

      <h3>Extras</h3>
      <BaseCheckbox label="Catering" v-model="event.extras.catering" />
      <BaseCheckbox label="Live music" v-model="event.extras.music" />

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
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
      event: {
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
    onSubmit() {},
  },
};
</script>
