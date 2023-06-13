<script lang="ts" setup>
// -----------------------------------
// test case 1: bug
// -----------------------------------
const { data } = await useAsyncData(async () => {
  const coreObject = ref({
    nestText: 'success',
  });
  const wrappar = ref({
    coreObject,
  });

  return {
    wrappar,
  };
});
if (!data.value) {
  throw new Error('data is undefined');
}
// value: success
// console error: TypeError: Cannot read properties of undefined (reading 'coreObject')
console.log(data.value.wrappar.coreObject.nestText);

// value: undefined
// no console error
console.log(data.value.wrappar.value.coreObject.nestText);
3;
// -----------------------------------
// test case 2: success
// -----------------------------------

const coreObject = ref({
  nestText: 'success',
});
const wrappar = ref({
  coreObject,
});

// value: success
console.log(wrappar.value.coreObject.nestText);
</script>

<template>
  <div>
    <NuxtWelcome />
  </div>
</template>
