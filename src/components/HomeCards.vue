<script setup>
import Card from "./Card.vue";
import CardLayout from "./CardLayout.vue";
</script>

<template>
  <section class="py-4">
    <div class="container-xl lg:container m-auto">
      <CardLayout>
        <Card />
        <Card
          bg="bg-green-100"
          title="For Employers"
          description="List your job to find the perfect developer for the role"
          link="/jobs/add"
          linkText="Add Job"
          buttonColor="bg-green-500"
        />
      </CardLayout>
    </div>
  </section>
</template>
