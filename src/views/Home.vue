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

      <BaseRadio label="Yes" v-model="event.pets" :value="1" name="pets" />
      <BaseRadio label="No" v-model="event.pets" :value="0" name="pets" />

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
};
</script>
