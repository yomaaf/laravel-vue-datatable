<template>
    <div>
        <div class="row">
            <div class="col-md-8">
                <h2 class="markdown-header">BelongsToMany Example</h2>
            </div>
            <div class="col-md-4 relative">
                <div class="show-code-inline">
                    <label>Show Example Code</label>&nbsp;
                    <vue-switch></vue-switch>
                </div>
            </div>
        </div>
        <information-alert>
            Note that the Datatable columnName attributes reflect their table name as well. This is to avoid integrity contraint violations caused by ambiguoius column selection.
        </information-alert>
        <pre v-highlightjs v-show="code">
            <belongs-to-many-php-markdown>
            </belongs-to-many-php-markdown>
            <belongs-to-many-js-markdown>
            </belongs-to-many-js-markdown>
        </pre>
        <data-table
            v-show="!code"
            :url="url"
            :columns="columns">
        </data-table>
    </div>
</template>

<script>

    import CodeExample from '../../../mixins/CodeExample';
    import DataTable from '../../../components/DataTable.vue';
    import VueSwitch from '../../../components/generic/Switch';
    import BasicMarkdown from '../../../markdown/examples/basic.md';
    import InformationAlert from '../../../components/generic/InformationAlert.vue';
    import DataTableSelectCell from '../../../components/generic/DataTableSelectCell.vue';
    import BelongsToManyJsMarkdown from '../../../markdown/examples/relationships/belongs-to-many-js.md';
    import BelongsToManyPhpMarkdown from '../../../markdown/examples/relationships/belongs-to-many-php.md';
    
    export default {
        name: 'Basic',
        components: {
            // eslint-disable-next-line
            DataTable,
            // eslint-disable-next-line
            VueSwitch,
            // eslint-disable-next-line
            BasicMarkdown,
            // eslint-disable-next-line
            InformationAlert,
            // eslint-disable-next-line
            DataTableSelectCell,
            // eslint-disable-next-line
            BelongsToManyJsMarkdown,
            // eslint-disable-next-line
            BelongsToManyPhpMarkdown,
        },
        mixins: [CodeExample],
        data() {
            return {
                name: 'BelongsToMany-Example',
                url: process.env.VUE_APP_ELOQUENT_URL,
                columns: [
                    {
                        label: 'ID',
                        name: 'id',
                        columnName: 'users.id',
                        orderable: true,
                    },
                    {
                        label: 'Name',
                        name: 'name',
                        columnName: 'users.name',
                        orderable: true,
                    },
                    {
                        label: 'Email',
                        name: 'email',
                        columnName: 'users.email',
                        orderable: true,
                    },
                    {
                        label: 'Departments',
                        name: 'departments',
                        columnName: 'departments.name',
                        component: DataTableSelectCell,
                        orderable: true,
                    },
                ]
            }
        },
    }
</script>
