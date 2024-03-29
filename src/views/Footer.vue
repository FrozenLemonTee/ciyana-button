<template>
  <transition name="fade" appear>
    <div class="footer">
      <div>
        <div class="author" style="margin: 4px auto auto">
          <div>©2021</div>
          <template v-for="(item, index) in author" :key="index">
            <a style="margin-left: 5px" v-if="index > 0">&</a>
            <a
              style="margin-left: 5px"
              :href="item.url"
              target="_blank"
              >{{ item.name }}</a
            >
          </template>
        </div>
        <div class="info">
          <div>{{ t(INFO_I18N.specialThanks1) }} <a href="https://github.com/vbup-osc">VBUP Open Source Community</a></div>
          <div>{{ t(INFO_I18N.specialThanks2) }} <a href="https://github.com/blacktunes/voices-button-cli" target="_blank">voices-button-cli</a>  |  {{ t(INFO_I18N.specialThanks3) }} <a href="https://pages.cloudflare.com/" target="_blank">Cloudflare Pages</a></div>
          <div><img style="margin: 5px 5px 0 -2px" alt="GitHub Repo stars" src="https://img.shields.io/github/stars/FrozenLemonTee/ciyana-button?style=social"><img style="margin: 5px 5px 0 -2px" alt="GitHub Repo forks" src="https://img.shields.io/github/forks/FrozenLemonTee/ciyana-button?style=social"></div>
          <template v-for="(item, index) in info" :key="index">
            <div v-html="item"></div>
          </template>
        </div>
      </div>
      <div class="text-right">
        <div><p></p></div>
        <div class="git">
          <IBtn
            class="btn"
            :url="githubUrl"
            :img="githubPng"
          />
          <a :href="githubUrl" target="_blank">{{ t(INFO_I18N.toGithub) }}</a>
        </div>
        <div>{{ t(INFO_I18N.notOfficial) }}</div>
        <img style="margin-top: 5px" alt="GitHub Repo license" src="https://img.shields.io/github/license/FrozenLemonTee/ciyana-button?style=social">
      </div>
    </div>
  </transition>
</template>

<script lang="ts">
import { useI18n } from 'vue-i18n'
import { INFO_I18N } from '@/assets/script/type'
import IBtn from '@/components/common/IconBtn.vue'
import Setting from '@/../setting/setting.json'
import githubPng from '@/assets/image/github-fill.png'

const FOOTER: {
  author?: {
    name: string;
    url?: string;
  }[];
  info?: string[];
  githubUrl?: string;
  belongTo?: string;
  poweredBy?: string;
  hostedOn?: string;
} = Setting['footer']

export default {
  components: {
    IBtn
  },
  setup() {
    const { t } = useI18n()

    return {
      INFO_I18N,
      t,
      author: FOOTER && FOOTER.author ? FOOTER.author : [],
      info: FOOTER && FOOTER.info ? FOOTER.info : [],
      githubUrl: FOOTER && FOOTER.githubUrl ? FOOTER.githubUrl : undefined,
      belongTo: FOOTER && FOOTER.belongTo ? FOOTER.belongTo : undefined,
      poweredBy: FOOTER && FOOTER.poweredBy ? FOOTER.poweredBy : undefined,
      hostedOn: FOOTER && FOOTER.hostedOn ? FOOTER.hostedOn : undefined,
      githubPng
    }
  }
}
</script>

<style lang="stylus" scoped>
.footer
  display flex
  justify-content space-between
  flex-wrap wrap
  padding 5px
  background-color #ebebeb
  font-size 12px
  color #333

  .author
    display flex
    align-items center

  .info
    margin-top 5px
    line-height 18px

  .text-right
    text-align right

    .git
      display flex
      align-items center

      a
        margin 0

      .btn
        margin 0 5px

@media only screen and (max-width 600px)
  .footer
    flex-direction column

    .text-right
      text-align left

      .git
        display flex
        align-items center

        .btn
          order 10

@media (prefers-color-scheme dark)
  .footer
    background-color #ddd
</style>
