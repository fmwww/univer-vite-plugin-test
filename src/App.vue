<script setup>
import {onMounted, ref} from 'vue';
import {Univer} from '@univerjs/core';
import {defaultTheme} from '@univerjs/design';
import {UniverRenderEnginePlugin} from '@univerjs/engine-render';
import {UniverFormulaEnginePlugin} from '@univerjs/engine-formula';
import {UniverUIPlugin} from '@univerjs/ui';
import {UniverDocsPlugin} from '@univerjs/docs';
import {UniverDocsUIPlugin} from '@univerjs/docs-ui';
import {UniverSheetsPlugin} from '@univerjs/sheets';
import {UniverSheetsUIPlugin} from '@univerjs/sheets-ui';
import {UniverSheetsFormulaPlugin} from '@univerjs/sheets-formula';

const univerRef = ref(null);

onMounted(() => {
  const univer = new Univer({
    theme: defaultTheme,
  });

// core plugins
  univer.registerPlugin(UniverRenderEnginePlugin);
  univer.registerPlugin(UniverFormulaEnginePlugin);
  univer.registerPlugin(UniverUIPlugin, {
    container: univerRef.value,
    header: true,
    toolbar: true,
    footer: true,
  });

// doc plugins
  univer.registerPlugin(UniverDocsPlugin, {
    hasScroll: false,
  });
  univer.registerPlugin(UniverDocsUIPlugin);

// sheet plugins
  univer.registerPlugin(UniverSheetsPlugin);
  univer.registerPlugin(UniverSheetsUIPlugin);
  univer.registerPlugin(UniverSheetsFormulaPlugin);

  univer.createUniverSheet({});
});
</script>

<template>
  <div ref="univerRef" style="width: 100%;height: 100%"></div>
</template>

<style scoped>
</style>
