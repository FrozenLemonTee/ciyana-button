<template>
  <template v-for="item in Player.voices.value" :key="item.name || item.title">
    <transition-group name="fade">
      <div v-if="Player.isShowCategory(item)">
        <Card>
          <template #header>
            <div class="category">
              <template v-if="Player.playSetting.showInfo">
                <a :href="item.url" target="_blank">{{
                  item.title === "unknown" ? t("unknown") : item.title
                }}</a>
              </template>
              <template v-else>
                {{ t(`voicecategory.${item.name}`) }}
              </template>
            </div>
          </template>
          <div class="content">
            <template v-for="voice in item.voiceList" :key="voice.name">
              <transition-group name="fade">
                <VBtn
                  v-if="Player.isShowVoice(voice)"
                  :title="Player.isShowTime(voice.mark)"
                  :text="t(`voice.${voice.name}`)"
                  :name="voice.name"
                  :newIcon="Player.isShowNewIcon(voice.date)"
                  :showPic="Player.getPicUrl(voice.usePicture)"
                  :ref="el => setBtnList(voice.name, el)"
                  @click.prevent="Player.play(voice)"
                />
              </transition-group>
            </template>
          </div>
        </Card>
      </div>
    </transition-group>
  </template>
</template>

<script lang="ts">
import { useI18n } from 'vue-i18n'
import Card from '../common/Card.vue'
import VBtn from '../common/VoiceBtn.vue'
import { getBtnList, useSearch, createPlayer, initListen } from './Player'

export default {
  components: {
    Card,
    VBtn
  },
  setup() {
    const { t } = useI18n()
    const { btnList, setBtnList } = getBtnList()
    const { searchData, highlight } = useSearch(btnList)
    const Player = createPlayer(btnList)
    initListen(btnList)

    return {
      t,
      setBtnList,
      searchData,
      highlight,
      Player
    }
  }
}

</script>
<style lang="stylus" scoped>
.category
  font-size 24px
  padding 14px 10px
  user-select none

.content
  display flex
  flex-wrap wrap
</style>
