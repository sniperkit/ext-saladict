<template>
  <div class="opt-item"><!-- 查词模式-->
    <div class="opt-item__header">
      <strong>{{ $t('opt:mode_title') }}</strong>
    </div>
    <div class="opt-item__body">
      <div class="checkbox">
        <label class="checkbox-inline">
          <input type="checkbox" v-model="mode.icon"> {{ $t('opt:mode_icon') }}
        </label>
        <label class="checkbox-inline">
          <input type="checkbox" v-model="mode.direct"> {{ $t('opt:mode_direct') }}
        </label>
        <label class="checkbox-inline">
          <input type="checkbox" v-model="mode.double"> {{ $t('opt:mode_double') }}
        </label>
        <label class="checkbox-inline">
          <input type="checkbox" v-model="mode.ctrl"> {{ $t('opt:mode_ctrl') }}
        </label>
        <label class="checkbox-inline">
          <input type="checkbox" v-model="mode.instant.enable"> {{ $t('opt:mode_instant') }}
        </label>
      </div>
      <div class="input-group" v-if="mode.double">
        <div class="input-group-addon">{{ $t('opt:mode_double_click_delay') }}</div>
        <input type="number" min="1" class="form-control" v-model.number="doubleClickDelay">
        <div class="input-group-addon">{{ $t('opt:unit_ms') }}</div>
      </div>
      <div class="instant-capture-container" v-if="mode.instant.enable">
        <label class="select-box">
          <span class="select-label">{{ $t('opt:mode_instant_key') }}</span>
          <select class="form-control" v-model="mode.instant.key">
            <option value="alt">{{ $t('opt:mode_instant_alt') }}</option>
            <option value="ctrl">{{ $t('opt:mode_instant_ctrl') }}</option>
            <option value="direct">{{ $t('opt:mode_instant_direct') }}</option>
          </select>
        </label>
        <div class="input-group instant-capture-delay">
          <div class="input-group-addon">{{ $t('opt:mode_instant_delay') }}</div>
          <input type="number" min="1" class="form-control" v-model.number="mode.instant.delay">
          <div class="input-group-addon">{{ $t('opt:unit_ms') }}</div>
        </div>
      </div>
    </div>
    <div class="opt-item__description-wrap">
      <p class="opt-item__description" v-html="$t('opt:mode_description')"></p>
    </div>
  </div><!-- 查词模式-->
</template>

<script>
export default {
  store: {
    mode: 'config.mode',
    doubleClickDelay: 'config.doubleClickDelay',
  }
}
</script>
