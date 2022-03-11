<template>
    <div :class="className">
        <ul class ="rating-box flex justify-between flex-nowrap items-center">
            <li v-for="(classes, index) in markClasses" :class="[classes]" :key="index">
                <svg width="24" height="22" viewBox="0 0 24 22" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12.746 0.463969L15.856 6.76397L22.81 7.77597C22.9636 7.79812 23.1079 7.86284 23.2266 7.9628C23.3453 8.06275 23.4337 8.19395 23.4817 8.34154C23.5296 8.48913 23.5353 8.6472 23.4981 8.79786C23.4609 8.94851 23.3822 9.08573 23.271 9.19397L18.238 14.094L19.426 21.02C19.4522 21.173 19.4351 21.3302 19.3766 21.474C19.3181 21.6177 19.2205 21.7423 19.095 21.8335C18.9694 21.9247 18.8208 21.979 18.666 21.9903C18.5112 22.0015 18.3564 21.9692 18.219 21.897L12 18.632L5.77996 21.9C5.64245 21.9718 5.48759 22.0039 5.33285 21.9924C5.1781 21.981 5.02963 21.9266 4.90415 21.8353C4.77867 21.7441 4.68118 21.6196 4.62267 21.4758C4.56415 21.3321 4.54694 21.1749 4.57296 21.022L5.76096 14.1L0.727965 9.19997C0.616754 9.09173 0.538074 8.95451 0.500838 8.80386C0.463602 8.6532 0.469297 8.49513 0.517278 8.34754C0.565259 8.19995 0.653609 8.06875 0.772321 7.96879C0.891033 7.86884 1.03536 7.80412 1.18897 7.78197L8.14296 6.76497L11.253 0.464969C11.3218 0.325796 11.4281 0.208617 11.5599 0.126653C11.6918 0.0446897 11.8439 0.0012028 11.9992 0.00109882C12.1544 0.000994836 12.3066 0.0442779 12.4385 0.126065C12.5705 0.207852 12.677 0.324888 12.746 0.463969Z" fill="#FF9D2A"/>
                </svg>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">

enum StarSize {
    middle = 'middleSize',
    small = 'smallSize',
}

enum MarkColor {
    active = 'orange',
    default = 'default',
}
export default {
    name:'star-rating',
    props: {
        small: {
            type: Boolean,
            default: true,
        },
        middle: {
            type: Boolean,
            default: false,
        },
        mark: {
            type: Number,
            default: 5,
        },
    },
    computed: {
         className() {
            return {
                'py-1': true,
                ...this.checkClasses()
            }
        },
        markClasses() {
            let marks = [];

            for (let i = 0; i < 5; i++) {
                if (i < Math.round(this.mark)) {
                    marks.push(MarkColor.active);
                    continue;
                }
                marks.push(MarkColor.default);
            }
            return marks;
        },
    },
    methods: {
        checkClasses() {
            let classes = {};
            
            if (this.middle) {
                classes[StarSize.middle] = true;
            } else {
                classes[StarSize.small] = true;
            }

            return classes;
        },
    },
    data: () => {
        return { }
    },
} 
</script>

<style scoped>
.rating-box li path {
    fill: theme('colors.gray.500');
}
.rating-box li.orange path {
    fill: theme('colors.orange.DEFAULT');
}
.middleSize {
   @apply sm:w-36 w-24;
}
.smallSize {
    @apply w-24;
}
.middleSize li svg {
    @apply sm:w-6 w-4 sm:h-6 h-4;
}
.smallSize li svg {
    @apply w-4 h-4;
}
</style>
