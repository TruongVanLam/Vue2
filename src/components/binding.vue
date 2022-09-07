<script>
export default {
    data() {
        return {
            message: '',
            text: '',
            checked: false,
            checkedNames: [],
            radioCheck: '',
            selected: '',
            multiSelected: [],
            options: [
                { text: 'Đọt bí xào tỏi', value: '50k' },
                { text: 'Canh bông điên điển', value: '30k' },
                { text: 'Lẩu nấm', value: '45k' }
            ]
        }
    }
}
</script>

<template>
    <div>
        <!-- text -->
        <span>Thong diep 1 dong:</span><br />
        <input v-model="message" placeholder="Hay nhap..." />
        <p> Thong diep da nhap: {{ message }}</p>
        <span>Thong diep co nhieu dong:</span><br />
        <textarea v-model="text" placeholder="Hay nhap nhieu dong..." style="width: 500px;"></textarea>
        <p style="white-space: pre-line;"> Thong diep da nhap: {{ text }}</p>

        <!-- checkbox -->
        <h2>Checkbox</h2>
        <input type="checkbox" id="checkbox" v-model="checked" />
        <label for="checkbox">{{ checked }}</label>

        <!-- multi checkbox -->
        <h2>Multi checkbox</h2>
        <div>
            <input type="checkbox" id="com-chien-toi" value="Cơm chiên tỏi" v-model="checkedNames">
            <label for="com-chien-toi">Cơm chiên tỏi</label><br>
            <input type="checkbox" id="dot-bi-xao-toi" value="Đọt bí xào tỏi" v-model="checkedNames">
            <label for="dot-bi-xao-toi">Đọt bí xào tỏi</label><br>
            <input type="checkbox" id="canh-rau-rung" value="Canh rau rừng" v-model="checkedNames">
            <label for="canh-rau-rung">Canh rau rừng</label>
            <br>
            <span>Món đã chọn: {{ checkedNames }}</span>
        </div>

        <!-- Radio -->
        <h2>Radio</h2>
        <input type="radio" id="cac-mon-rau" value="Các món rau" v-model="radioCheck" />
        <label for="cac-mon-rau">Các món rau</label><br>
        <input type="radio" id="cac-mon-thit" value="Các món thịt" v-model="radioCheck" />
        <label for="cac-mon-thit">Các món thịt</label><br>
        <span>Đã chọn: {{ radioCheck }}</span>

        <!-- Select -->
        <h2>Single select</h2>
        <div>Món đã chọn: {{ selected }}</div>
        <select v-model="selected">
            <option disabled value="">Vui lòng chọn món</option>
            <option>Cơm rang</option>
            <option>Phở</option>
            <option>Mì</option>
        </select>

        <h2>Multiple select</h2>
        <div>Các món đã chọn: {{ multiSelected }}</div>
        <select v-model="multiSelected" multiple>
            <option>Cơm rang</option>
            <option>Phở</option>
            <option>Mì</option>
        </select>

        <h2>Render <code style="color: red;">option</code> với <code style="color: red;">v-for</code></h2>
        <select v-model="selected">
            <option v-for="option in options" :value="option.value">{{ option.text }}</option>
        </select>
        <span>Giá tiền: {{selected}}</span>

        <!-- Value Bindings -->
    </div>
</template>