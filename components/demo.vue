<template>
    <Toast />
    <ConfirmPopup group="headless">
        <template #container="{ message }">
            <div class="rounded p-4">
                <span>{{ message.message }}</span>
                <div class="w-full p-1 flex gap-2 pl-5">
                    <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === 'week' }" class="rounded-md px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLastWeek">7 Days</button>
                    <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === '15days' }" class="rounded-md px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLast15Days">15 Days</button>
                    <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === 'month' }" class="rounded-md px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLastMonth">Month</button>
                    <button type="button" :class="{ 'bg-blue-500 text-white': activeFilter === '3months' }" class="rounded-md px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300" @click="filterLast3Months">3 Months</button>
                </div>

                <div class="flex items-center gap-2 mt-4">
                    <Button label="Save" @click="acceptCallback" size="small"></Button>
                    <Button label="Cancel" outlined @click="rejectCallback" severity="secondary" size="small" text></Button>
                </div>
            </div>
        </template>
    </ConfirmPopup>
    <div class="card flex justify-center">
        <Button @click="requireConfirmation($event)" label="Save"></Button>
    </div>
</template>

<script setup>
import { ref } from "vue";
import { useConfirm } from "primevue/useconfirm";
import { useToast } from "primevue/usetoast";

const confirm = useConfirm();
const toast = useToast();
const activeFilter = ref("");

const requireConfirmation = (event) => {
    confirm.require({
        target: event.currentTarget,
        group: 'headless',
        message: 'Save your current process?',
        accept: () => {
            toast.add({ severity: 'info', summary: 'Confirmed', detail: 'You have accepted', life: 3000 });
        },
        reject: () => {
            toast.add({ severity: 'error', summary: 'Rejected', detail: 'You have rejected', life: 3000 });
        }
    });
};

const closeModal = () => {
    confirm.close();
};

const filterLastWeek = () => {
    activeFilter.value = "week";
    closeModal();
};

const filterLast15Days = () => {
    activeFilter.value = "15days";
    closeModal();
};

const filterLastMonth = () => {
    activeFilter.value = "month";
    closeModal();
};

const filterLast3Months = () => {
    activeFilter.value = "3months";
    closeModal();
};
</script>
