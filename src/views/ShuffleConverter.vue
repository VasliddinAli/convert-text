<template>
    <div>
        <div class="head">
            <h4 v-for="item in basicArray" :key="item" class="harf">{{ item }}</h4>
        </div>
        <h5>Kombinatsiyalar</h5>
        <form class="section" @submit.prevent>
            <div>
                <input id="Section1" type="radio" value="Section1" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section1)" class="sectionInput" />
                <label for="Section1" class="sectionLabel">1</label>
            </div>
            <div>
                <input id="Section2" type="radio" value="Section2" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section2)" class="sectionInput" />
                <label for="Section2" class="sectionLabel">2</label>
            </div>
            <div>
                <input id="Section3" type="radio" value="Section3" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section3)" class="sectionInput" />
                <label for="Section3" class="sectionLabel">3</label>
            </div>
            <div>
                <input id="Section4" type="radio" value="Section4" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section4)" class="sectionInput" />
                <label for="Section4" class="sectionLabel">4</label>
            </div>
            <div>
                <input id="Section5" type="radio" value="Section5" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section5)" class="sectionInput" />
                <label for="Section5" class="sectionLabel">5</label>
            </div>
            <div>
                <input id="Section6" type="radio" value="Section6" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section6)" class="sectionInput" />
                <label for="Section6" class="sectionLabel">6</label>
            </div>
            <div>
                <input id="Section7" type="radio" value="Section7" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section7)" class="sectionInput" />
                <label for="Section7" class="sectionLabel">7</label>
            </div>
            <div>
                <input id="Section8" type="radio" value="Section8" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section8)" class="sectionInput" />
                <label for="Section8" class="sectionLabel">8</label>
            </div>
            <div>
                <input id="Section9" type="radio" value="Section9" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section9)" class="sectionInput" />
                <label for="Section9" class="sectionLabel">9</label>
            </div>
            <div>
                <input id="Section10" type="radio" value="Section10" v-model="selectedSection"
                    @change="selectedSectionChange(shuffledArrays.Section10)" class="sectionInput" />
                <label for="Section10" class="sectionLabel">10</label>
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
                Section1: ["M", "Y", "H", "T", "S", "W", "K", "D", "O", "G", "Q", "J", "F", "Z", "C", "U", "N", "B", "P", "A", "V", "I", "R", "X", "L", "E"],
                Section2: ["C", "H", "I", "L", "N", "B", "K", "J", "U", "Z", "O", "X", "Q", "Y", "R", "D", "V", "E", "A", "S", "F", "G", "M", "P", "T", "W"],
                Section3: ["G", "M", "P", "R", "N", "W", "Q", "C", "L", "F", "A", "U", "E", "Z", "K", "J", "T", "B", "H", "S", "O", "X", "Y", "I", "D", "V"],
                Section4: ["H", "B", "R", "Q", "K", "D", "M", "P", "L", "E", "I", "O", "A", "G", "F", "N", "C", "T", "V", "Y", "X", "U", "Z", "W", "J", "S"],
                Section5: ["S", "M", "P", "W", "D", "L", "R", "E", "G", "N", "A", "C", "F", "B", "T", "V", "Y", "U", "Q", "O", "X", "J", "H", "K", "Z", "I"],
                Section6: ["J", "T", "H", "N", "X", "I", "D", "A", "M", "B", "P", "W", "K", "R", "S", "Q", "O", "C", "F", "V", "U", "L", "Z", "E", "G", "Y"],
                Section7: ["L", "H", "P", "G", "Q", "F", "V", "A", "O", "S", "M", "K", "N", "C", "U", "E", "X", "T", "I", "W", "D", "R", "Y", "B", "J", "Z"],
                Section8: ["W", "R", "B", "S", "F", "P", "T", "H", "J", "E", "Y", "G", "N", "A", "K", "Z", "C", "I", "V", "M", "D", "O", "U", "Q", "L", "X"],
                Section9: ["U", "N", "W", "G", "V", "A", "B", "S", "J", "H", "D", "O", "R", "E", "Y", "T", "L", "P", "K", "I", "X", "Q", "Z", "M", "C", "F"],
                Section10: ["O", "S", "I", "C", "U", "E", "L", "K", "P", "W", "N", "T", "Q", "X", "F", "D", "H", "J", "V", "G", "A", "B", "R", "Y", "M", "Z"],
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
h5 {
    padding: 0;
    margin: 0;
    padding-bottom: 20px;
    text-align: center;
    font-size: 20px;
}

.head {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding-bottom: 15px;
    padding-top: 15px;
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
    font-weight: bold;
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