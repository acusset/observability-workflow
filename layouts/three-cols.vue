<template>
  <div class="slidev-layout three-cols">
    <slot />
    <div class="cols-wrapper">
      <div class="col col-left">
        <slot name="left" />
      </div>
      <div class="col col-center">
        <slot name="center" />
      </div>
      <div class="col col-right">
        <slot name="right" />
      </div>
    </div>
  </div>
</template>

<style>
.three-cols {
  display: flex;
  flex-direction: column;
  height: 100%;
  padding: 1rem 2rem;
}

.three-cols .cols-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1.5rem;
  flex: 1;
  margin-top: 1rem;
}

.three-cols .col {
  overflow: auto;
}
</style>
