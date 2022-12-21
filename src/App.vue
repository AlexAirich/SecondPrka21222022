<template>
    <div class="app"> 
        <EmployeeForm
            @check="checkInput"
        ></EmployeeForm>

        <EmployeeList 
            :employees="employees"
            @remove="removeEmployee"
        ></EmployeeList>

    <p>Итого без налоговых вычетов: {{ totalWithoutTax }}₸</p>
    <p>Итого с налоговыми вычетами: {{ totalWithTax }}₸</p>
  </div>
</template>
<script>

import EmployeeForm from "@/components/EmployeeForm.vue";
import EmployeeList from "@/components/EmployeeList.vue";

export default {

    components: {
        EmployeeForm, EmployeeList
    },

    data() {
        return {
            employees: [                
                {fullName: "Айрих Алексей Алексеевич", date: "21-11-2022", daysWork: 16, salary: 200000},
                {fullName: "Капирбек Альмансур Бексултанович", date: "15-11-2022", daysWork: 54, salary: 150000},
                {fullName: "Сафонов Сергей Иванович", date: "24-11-2022", daysWork: 19, salary: 300000},],
        }
    },
    methods: {

        addEmployee () {

        },


        checkInput (employees) {
            
            if (employees.inputFullName == "") {
                document.querySelector("#name").classList.add("empty")
                return
            }
            if (employees.inputDate == "") {
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.add("empty")
                return
            }
            if (employees.inputDaysWork == "") {
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.remove("empty")
                document.querySelector("#work").classList.add("empty")
                return
            }
            if (employees.inputSalary == "") {
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.remove("empty")
                document.querySelector("#work").classList.remove("empty")
                document.querySelector("#salary").classList.add("empty")
                return
            }
            else 
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.remove("empty")
                document.querySelector("#work").classList.remove("empty")
                document.querySelector("#salary").classList.remove("empty")
                this.employees.push({
                    fullName: employees.inputFullName,
                    date: employees.inputDate,
                    daysWork: employees.inputDaysWork,
                    salary: employees.inputSalary,
                });
                    employees.inputFullName = ""
                    employees.inputDate = ""
                    employees.inputDaysWork = ""
                    employees.inputSalary = ""
                    console.log(this.employees) 
                    
        },

        removeEmployee (employees, index) {
            employees.splice(index, 1)
            this.totalPrice()
        },

        totalPrice () {

        }
        
    },
            computed: {
    totalWithoutTax() {
      return this.employees.reduce((acc, employees) => acc + employees.salary, 0)
    },
    totalWithTax() {
      return this.employees.reduce((acc, employees) => acc + employees.salary * 0.85, 0)
    }
  }
}
</script>
<style>
      input{
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;  
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}
  div {
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
}
</style>