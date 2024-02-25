<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Front End</template>

    Lorem ipsum
    <a href="https://si.stechoq.com/" target="_blank" rel="noopener">dolor sit amet</a>
    consectetur, adipisicing elit.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Back End</template>

    Lorem ipsum dolor sit amet consectetur,
    <a href="https://si.stechoq.com/" target="_blank" rel="noopener">adipisicing elit.</a>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Artificial Intelligence</template>

    Lorem ipsum
    <a href="https://si.stechoq.com/" target="_blank" rel="noopener">dolor sit amet</a>
    consectetur, adipisicing elit.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>UI/UX</template>

    Lorem ipsum dolor sit amet consectetur,
    <a href="https://si.stechoq.com/" target="_blank" rel="noopener">adipisicing elit.</a>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Community Support</template>

    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Suscipit eaque pariatur accusantium
    veniam sed quae,
    <a href="https://si.stechoq.com/" target="_blank" rel="noopener">harum ex adipisci?</a>
    Sunt, perferendis excepturi quam illo unde commodi ut perspiciatis adipisci dolorem nulla.
  </WelcomeItem>
</template>
