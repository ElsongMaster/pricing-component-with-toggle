<template>
  <div
    class="card-price bg-white  rounded-lg mx-auto p-6 border-1"
    style="width: 300px; height: 60vh; border: 1px solid rgb(219,219,219); box-shadow:1px 1px 1px 1px rgb(219,219,219);"
  >
    <p class="title-package font-bold text-gray-500  my-2">{{ titlePackage }}</p>
    <div class="package-price ">
      <p class="price my-2 text-5xl font-bold text-gray-600 flex justify-center items-center " ><span class=" text-3xl flex justify-end " style="  ">$</span>{{ price }}</p>
    </div>
    <div class="storage border-t-2">
      <p class="my-2 font-bold text-gray-500">{{ storageCapacity }} Storage</p>
    </div>
    <div class="users border-t-2">
      <p class="my-2 font-bold text-gray-500">{{ usersNb }} Users Allowed</p>
    </div>
    <div class="sendUp border-t-2 border-b-2">
      <p class="my-2 font-bold text-gray-500">Send up to {{ sendupCapacity }}</p>
    </div>

    <!-- <div class="linkBtn border-t-2">
    </div> -->
      <a
        :href="link"
        class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
        >LEARN MORE</a
      >
  </div>
</template>

<script>
export default {
  name: "CardPrice",
  props: [
    "titlePackage",
    "price",
    "storageCapacity",
    "usersNb",
    "sendupCapacity",
    "link",
  ],
};
</script>

<style></style>
