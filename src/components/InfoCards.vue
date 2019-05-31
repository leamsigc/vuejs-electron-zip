<template>
  <div class="card">
    <h1 class="card__title">{{codeInfo[0]['place name']}}</h1>
    <div class="card__location">{{codeInfo[0]['state']}}, {{codeInfo[0]['state abbreviation']}}</div>
    <div class="card__long">
      <strong>Longitude:</strong>
      {{codeInfo[0]['longitude']}}
    </div>
    <div class="card__lat">
      <strong>Latitude:</strong>
      {{codeInfo[0]['latitude']}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'InfoCard',
  props: ['codeInfo'],
};
</script>

<style>
.card {
  border: 1px solid #625aca;
  padding: 2rem 1rem;
  max-width: 300px;
  margin: 0 auto;
  background: rgba(98, 90, 202, 0.4);
  color: #fefefe;
  border-radius: 5px;
  box-shadow: 0.5rem 0.5rem 0.5rem -0.5rem #625aca;
}
</style>
