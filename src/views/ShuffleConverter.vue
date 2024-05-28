<template>
    <div>
        <div class="head">
            <h4 v-for="item in basicArray" :key="item" class="harf">{{ item }}</h4>
        </div>
        <form class="section" @submit.prevent>
            <div>
                <input id="Section1" type="radio" value="Section1" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section1)" class="sectionInput" />
                <label for="Section1" class="sectionLabel">Section1</label>
            </div>
            <div>
                <input id="Section2" type="radio" value="Section2" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section2)" class="sectionInput" />
                <label for="Section2" class="sectionLabel">Section2</label>
            </div>
            <div>
                <input id="Section3" type="radio" value="Section3" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section3)" class="sectionInput" />
                <label for="Section3" class="sectionLabel">Section3</label>
            </div>
        </form>
        <div class="head" v-if="arrayData != null">
            <h4 v-for="item in arrayData" :key="item" class="harf">{{ item }}</h4>
        </div>
        <div class="inputs">
            <textarea v-model="inputText" placeholder="Matn kiriting..."></textarea>
            <textarea :value="outputText" readonly></textarea>
        </div>
        <div class="btns">
            <button @click="convertText">Shifrlash</button>
            <button @click="revertText">Deshifrlash</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            basicArray: [
                "A",
                "B",
                "C",
                "D",
                "E",
                "F",
                "G",
                "H",
                "I",
                "J",
                "K",
                "L",
                "M",
                "N",
                "O",
                "P",
                "Q",
                "R",
                "S",
                "T",
                "U",
                "V",
                "W",
                "X",
                "Y",
                "Z",
            ],
            shuffledArrays: {
                Section1: ["M", "Y", "H", "T", "S", "W", "K", "D", "G", "Q", "J", "F", "Z", "C", "O", "U", "N", "B", "P", "A", "V", "I", "R", "X", "L", "E"],
                Section2: ["C", "H", "I", "L", "N", "B", "K", "J", "U", "Z", "O", "X", "Q", "Y", "R", "D", "V", "E", "A", "S", "F", "G", "M", "P", "T", "W"],
                Section3: ["G", "M", "P", "R", "N", "W", "Q", "C", "L", "F", "A", "U", "E", "Z", "K", "J", "T", "B", "H", "S", "O", "X", "Y", "I", "D", "V"]
            },
            selectedSection: '',
            inputText: '',
            outputText: '',
            selectedArray: '',
            arrayData: null,
        };
    },
    methods: {
        selectedSectionChange(val) {
            this.arrayData = val
            console.log(val);
        },
        convertText() {
            if (!this.selectedSection) {
                alert('Iltimos, avval bir bo‘limni tanlang');
                return;
            }
            const selectedArray = this.shuffledArrays[this.selectedSection];
            const inputArray = this.inputText.toUpperCase().split('');
            this.outputText = inputArray.map(char => {
                const index = this.basicArray.indexOf(char);
                return index !== -1 ? selectedArray[index] : char;
            }).join('');
        },
        revertText() {
            if (!this.selectedSection) {
                alert('Iltimos, avval bir bo‘limni tanlang');
                return;
            }
            const selectedArray = this.shuffledArrays[this.selectedSection];
            const outputArray = this.inputText.split('');
            this.outputText = outputArray.map(char => {
                const index = selectedArray.indexOf(char.toUpperCase());
                return index !== -1 ? this.basicArray[index] : char;
            }).join('');
        }
    }
};
</script>

<style scoped>
.head {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding-bottom: 20px;
    padding-top: 20px;
}

.inputs {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.harf {
    padding: 0;
    margin: 0;
    width: 30px;
    height: 30px;
    border: 1px solid #777;
    border-radius: 5px;
    font-size: 16px;
    font-weight: 999;
    display: flex;
    align-items: center;
    justify-content: center;
}

.btns {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.btns button {
    border: 1px solid #d3d3d3;
    background-color: #f5f5f5;
    padding: 5px 30px;
    cursor: pointer;
    text-align: center;
    border-radius: 4px;
    font-size: 16px;
}

.btns button:nth-child(2) {
    background-color: #ff0000;
    color: #fff
}

textarea {
    display: block;
    width: 100%;
    height: 100px;
    margin-top: 10px;
    margin-bottom: 10px;
    resize: none;
}

button {
    display: block;
    margin-bottom: 10px;
}

.section {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.sectionLabel {
    border: 1px solid #d3d3d3;
    background-color: #f5f5f5;
    padding: 5px 10px;
    cursor: pointer;
    width: 100%;
    text-align: center;
    border-radius: 4px;
}

.sectionInput {
    opacity: 0;
    position: fixed;
    width: 0;
}

.sectionInput:checked+label {
    background-color: #5e50ee;
    border-color: #5e50ee;
    color: #fff;
}
</style>