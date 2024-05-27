<script setup>
import { defineProps } from 'vue';
defineProps(['character']);
</script>

<template>
  <div class="modal fade" id="evilModal" data-backdrop="static" data-keyboard="false" tabindex="-1" aria-labelledby="evilModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="evilModalLabel">Acerca de: {{ character.name }} ({{ character.origin.name }})</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">

          <div class="row">
            <div class="col-6">
              <img :src="character.image" alt="..." class="w-100">
            </div>
            <div class="col-6">
              <p>
                <b>Gender</b>: {{ character.gender }}
              </p>
              <p>
                <b>Status</b>: {{ character.status }}
              </p>
              <p>
                <b>Specie</b>: {{ character.species }}
              </p>
            </div>
          </div>

        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary w-100" data-dismiss="modal">Cerrar</button>
          <!-- <button type="button" class="btn btn-primary">Understood</button> -->
        </div>
      </div>
    </div>
  </div>
</template>