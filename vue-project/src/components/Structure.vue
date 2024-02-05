<template>
  <beginning class="beginning">
    <slot name="beginning"></slot>
  </beginning>
  <medium class="medium">
    <slot name="medium"></slot>
  </medium>
  <end class="end">
    <slot name="end"></slot>
  </end>
  <end class="firstName">
    <slot name="firstName"></slot>
  </end>
</template>

<style>
.beginning {
  color: green;
}
.medium {
  color: blue;
}
.end {
  color: red;
}
.name {
  color: purple;
}
</style>
