<template>
  <div class="experience-box">
      <timeline-header :is_final=is_final />
      <div class="experience-content">
        <experiences-header :role=role :company=company :location=location :period=period />
        <paragraph v-for="(paragraph,index) in descriptions" :key="index" :paragraph=paragraph />
        <StackTag v-for="(stack, index) in stacks" :key="index" :stack="stack" />
      </div>
      <div class="empty-padding"></div>
  </div>
</template>
<script>
import TimelineHeader from '../atoms/TimelineHeader'
import Paragraph from '../atoms/Paragraph'
import ExperiencesHeader from '../atoms/ExperiencesHeader'
import StackTag from '../atoms/StackTag'

export default {
    name: 'ExperienceBox',
    components:{
        TimelineHeader,
        Paragraph,
        ExperiencesHeader,
        StackTag
    },
    props: {
        is_final: {
            type: Boolean,
            deafult: false
        },
        role: String,
        company: String,
        location: String,
        period: String,
        descriptions: String,
        stacks: Array
    }
}
</script>

<style scoped>
.experience-box {
    position: relative;
    width: 100%;
    min-height: 200px;
    animation: transitionIn 0.8s linear;
}

.experience-content {
    margin-left: 60px;
    margin-right: 20px;
    background: var(--secondary-bg-color);
    padding: 20px;
    transition: 0.25s;
}

.experience-content:hover {
    transform: scale(1.05);
}

.empty-padding {
    padding: 10px;
}

@keyframes transitionIn {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

@media(max-width:768px) {
    .experience-content {
        margin-left: 0px;
        margin-right: 0px;
    }
}
</style>