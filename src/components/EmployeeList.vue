<template>

    <div class="employees-list" v-for="(employee, index) in employees">
        <div class="employee">
        <span>Порядковый номер: {{index + 1}}</span> <br>
        <span>ФИО: {{employee.fullName}}</span> <br>
        <span>Дата выдачи зарплаты: {{employee.date}}</span> <br>
        <span>Количество отработанных дней: {{employee.daysWork}}</span> <br>
        <span>Сумма заработной платы сотрудника без налоговых отчислений: {{employee.salary}}₸</span> <br>
        <span>Сумма заработной платы сотрудника с налоговыми отчислениями: {{Math.trunc(employee.salary - (employee.salary * 0.15))}}₸</span> <br>
            <div class="remove">
                <button type="button" name="plus" class="btn btn-delete" @click="removeEmployee(index)">Удалить</button>
            </div>
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
    methods: {
        removeEmployee (index) {
            this.$emit("remove", this.employees, index)
        }
    }
}
</script>
<style scoped>
	.employees-list{
    margin: 20px 0;
    padding: 10px;
    border: 2px solid black;
    border-radius: 10px;text-align:center;                                                                                                                                
	}

.btn-delete{
  width: 100%;
  background-color: #c52121;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.btn-delete:hover{
  background-color: #8b1d1d;
}
</style>


