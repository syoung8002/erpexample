<template>
    <div class="panel">
        <div class="label-title">{{label}}</div>
        <div class="table-responsive">
            <v-btn v-if="editMode" @click="addDetailRow()">추가</v-btn>
            <v-btn v-if="editMode" style="margin-left: 3px;" @click="detailDeleteRow()">삭제</v-btn>
            <v-table v-if="!editMode">
                <thead>
                    <tr>
                        <th>Id</th>
                        <th>ItemId</th>
                        <th>UnitPrice</th>
                        <th>qty</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(detailVal, idx) in selectedRow.salesItem" :key="detailVal" >
                        <td class="font-semibold">{{ idx + 1 }}</td>
                        <td class="whitespace-nowrap">
                            <ItemId v-model="detailVal.itemId" :editMode="editMode"/>
                        </td>
                        <td class="whitespace-nowrap">
                            <UnitPrice v-model="detailVal.unitPrice" :editMode="editMode"/>
                        </td>
                        <td class="whitespace-nowrap">{{ detailVal.qty }}</td>
                        <td class="whitespace-nowrap">
                            <Icon icon="mi:delete" @click="deleteRow(detailVal)" />
                        </td>
                    </tr>
                </tbody>
            </v-table>
            <v-table v-else>
                <thead>
                    <tr>
                        <th>Id</th>
                        <th>ItemId</th>
                        <th>UnitPrice</th>
                        <th>qty</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(addVal, idx) in newValue" :key="addVal" >
                        <td class="font-semibold">{{ idx + 1 }}</td>
                        <td class="whitespace-nowrap">
                            <ItemId v-model="addVal.itemId" :editMode="editMode"/>
                        </td>
                        <td class="whitespace-nowrap">
                            <UnitPrice v-model="addVal.unitPrice" :editMode="editMode"/>
                        </td>
                        <td class="whitespace-nowrap">
                            <Number style="margin-left: -5px; width: 150px;" :editMode="editMode" v-model="addVal.qty"/>
                        </td>
                    </tr>
                </tbody>
            </v-table>
        </div>
    </div>
</template>

<script>
import BaseDetailGrid from '../base-ui/BaseDetailGrid.vue';
import Number from '../primitives/Number.vue'

export default {
    name: 'PurchaseDetail',
    mixins: [BaseDetailGrid],
    components: {
        Number,
    },
    props: {
        label: String,
        editMode: Boolean,
        selectedRow: Object,
    },
    data: ()=>({
    }),
    created(){
    },
    methods: {
    }
}
</script>
