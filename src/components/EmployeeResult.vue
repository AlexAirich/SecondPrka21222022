<template>

    <div class="total-salary">
        <div class="alert alert-primary" role="alert">
          Общая сумма заработных плат сотрудников без налоговых: <strong>{{totalSalary}}₸</strong>
        </div>
    </div>

    <div class="total-salaryWithNalog">
        <div class="alert alert-primary" role="alert">
          Общая сумма заработных плат сотрудников с налогами: <strong>{{totalSalarytax}}₸</strong>
        </div>
    </div>

</template>
<script>
export default {
    props: {
        employees: {
            type: Array,
            required: true
        }
    },    
    data() {
        return {
            totalSalary: 0,
            totalSalarytax: 0
        }
    },
    methods: {
        totalPrice () {
            this.totalSalary = 0;
            this.totalSalarytax = 0;
            for (let i in this.employees) {
            let salarys = this.employees[i].salary
            this.totalSalary += salarys
            this.totalSalarytax += salarys - (salarys * 0.15)
            }
        }
    },
    mounted() {
        this.totalPrice()
    },
}
</script>
<style scoped>
    
</style>

