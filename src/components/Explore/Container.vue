<script lang="ts" setup>
// Components
import ExploreItem from "./Item.vue";

const props = withDefaults(
  defineProps<{
    type?: "profile" | "explore";
  }>(),
  {
    type: "explore",
  }
);

const getItemCount = () => {
  if (props.type === "profile") return 3;
  else return 4;
};
</script>

<template>
  <div
    class="space-y-px"
    :class="{
      'pt-4': type === 'explore',
      'pt-1': type === 'profile',
    }"
  >
    <div
      v-for="index in 6"
      :key="`wrapper-${index}`"
      class="flex gap-px"
      :class="{
        'overflow-x-hidden': type === 'explore',
        'flex-row-reverse': type === 'explore' && index % 2 === 0,
      }"
    >
      <div
        class="grid gap-px"
        :class="{
          'grid-cols-2 flex-shrink-0 grid-rows-2 place-items-stretch':
            type === 'explore',
          'grid-cols-3': type === 'profile',
        }"
      >
        <ExploreItem
          v-for="i in getItemCount()"
          :key="i"
          :image="`https://picsum.photos/id/${index}${i}/200/200`"
          :type="type === 'profile' ? 'profile' : 'small'"
        />
      </div>

      <ExploreItem
        v-if="type === 'explore'"
        type="large"
        :image="`https://www.google.com/imgres?imgurl=https%3A%2F%2Fimages.pexels.com%2Fphotos%2F110854%2Fpexels-photo-110854.jpeg%3Fauto%3Dcompress%26cs%3Dtinysrgb%26dpr%3D1%26w%3D500&imgrefurl=https%3A%2F%2Fwww.pexels.com%2Fsearch%2Fcosmic%2F&tbnid=N6vhdgyz0ZYK-M&vet=12ahUKEwjRxpuLi9f9AhXroP0HHffWB6EQMygAegUIARDgAQ..i&docid=HD616jUmEJ6NbM&w=500&h=365&q=cosmic&ved=2ahUKEwjRxpuLi9f9AhXroP0HHffWB6EQMygAegUIARDgAQ`"
      />
    </div>
  </div>
</template>
