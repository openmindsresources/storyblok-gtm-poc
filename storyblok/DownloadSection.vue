<template>
<section class="max-w-4xl mx-auto px-4 mb-12">
    <h2 class="text-2xl font-bold mb-4 text-blue-700">{{ title }}</h2>
    <div class="flex flex-col sm:flex-row sm:flex-wrap gap-4">
        <DownloadItem
            v-for="(item, idx) in items"
            :key="idx"
            :title="item.title"
            :description="item.description"
            :filename="item.filename"
            :group="title"
            :url="item.url"
        />
    </div>
    <div v-if="!disableViewAll" class="mt-6 flex justify-end">
        <a
            href="/e-library"
            data-tag="view_all_elibrary"
            v-bind:data-group="title"
            class="inline-block px-6 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 transition"
        >
            View More
        </a>
    </div>
</section>
</template>

<script setup>
import DownloadItem from './DownloadItem.vue'

const downloads = {
    technicalDatasheets: [
        {
            title: 'Certificate Document',
            description: 'Technical Datasheet | ExampleBrand®',
            filename: 'Certificate_Document.pdf',
            url: 'https://example.com/downloads/Certificate_Document.pdf'
        },
        {
            title: 'Safety Data Sheet',
            description: 'Material safety and handling information',
            filename: 'Safety_Data_Sheet.pdf',
            url: 'https://example.com/downloads/Safety_Data_Sheet.pdf'
        },
        {
            title: 'Installation Guide',
            description: 'Step-by-step installation instructions',
            filename: 'Installation_Guide.pdf',
            url: 'https://example.com/downloads/Installation_Guide.pdf'
        },
        {
            title: 'Performance Report',
            description: 'Detailed product performance analysis',
            filename: 'Performance_Report.pdf',
            url: 'https://example.com/downloads/Performance_Report.pdf'
        },
        {
            title: 'Compliance Certificate',
            description: 'Product compliance and certification details',
            filename: 'Compliance_Certificate.pdf',
            url: 'https://example.com/downloads/Compliance_Certificate.pdf'
        },
        {
            title: 'Warranty Statement',
            description: 'Warranty terms and conditions',
            filename: 'Warranty_Statement.pdf',
            url: 'https://example.com/downloads/Warranty_Statement.pdf'
        },
    ],
    brochures: [
        {
            title: 'Product Brochure',
            description: 'Comprehensive product overview and features',
            filename: 'Product_Brochure.pdf',
            url: 'https://example.com/downloads/Product_Brochure.pdf'
        },
        {
            title: 'Company Profile',
            description: 'Learn more about our company and values',
            filename: 'Company_Profile.pdf',
            url: 'https://example.com/downloads/Company_Profile.pdf'
        },
        {
            title: 'Case Studies',
            description: 'Real-world examples of our solutions in action',
            filename: 'Case_Studies.pdf',
            url: 'https://example.com/downloads/Case_Studies.pdf'
        },
        {
            title: 'Product Catalog',
            description: 'Detailed catalog of all available products',
            filename: 'Product_Catalog.pdf',
            url: 'https://example.com/downloads/Product_Catalog.pdf'
        },
        {
            title: 'Application Guide',
            description: 'Best practices and application recommendations',
            filename: 'Application_Guide.pdf',
            url: 'https://example.com/downloads/Application_Guide.pdf'
        },
        {
            title: 'Sustainability Report',
            description: 'Our commitment to sustainability and the environment',
            filename: 'Sustainability_Report.pdf',
            url: 'https://example.com/downloads/Sustainability_Report.pdf'
        },
    ],
}

const props = defineProps({
    title: {
        type: String,
        default: 'Downloads',
    },
    type: {
        type: String,
        default: 'brochure', // or 'technicalDatasheet'
        validator: value => ['brochure', 'technicalDatasheet'].includes(value),
    },
    disableViewAll: {
        type: Boolean,
        default: false,
    },
})

const items = computed(() => {
    if (props.type === 'technicalDatasheet') {
        return downloads.technicalDatasheets
    }
    return downloads.brochures
})
</script>
