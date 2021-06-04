<template>
  <div class="homepage">
    <section v-for="(section,indx) in homepage.section" :id="section.cssId" :key="indx">
      <slider v-if="section.__component == 'groups.slick-slide-group'" :sliderdata="section.Slick_slide_item" />
      <services v-if="section.__component == 'groups.service-group'" :servicesdata="section.service_item" />
      <doucks v-if="section.__component == 'groups.doucks-group'" :doucksdataleft="section.doucksleft" :doucksdataright="section.doucksright" />
    </section>
  </div>
</template>

<script>
export default {
  async asyncData ({ $strapi }) {
    const homepage = await $strapi.find('homepage')
    console.log(homepage)
    return { homepage }
  }
}
</script>
