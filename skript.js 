const API_URL = "sheetdb.io"; 

async function tolovniSaqlash() {
    const ismInput = document.getElementById('bolaIsmi');
    const summaInput = document.getElementById('summa');
    const bolaIsmi = ismInput.value;
    const summa = summaInput.value;
    const sana = new Date().toLocaleString('uz-UZ');

    if (bolaIsmi && summa) {
        const data = {
            "data": {
                "Bola ismi": bolaIsmi, 
                "Summa": summa,
                "Sana": sana
            }
        };

        await fetch(API_URL, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(data)
        });

        ismInput.value = '';
        summaInput.value = '';
        yangilash(); 
    }
}

async function yangilash() {
    const royxatDiv = document.getElementById('royxat');
    royxatDiv.innerHTML = 'Yuklanmoqda...';

    // Bu yerga kichik o'zgarish kiritildi
    const response = await fetch(API_URL + "?sheet=Sheet1");
    const data = await response.json();

    royxatDiv.innerHTML = '';
    data.reverse().forEach(item => {
        const div = document.createElement('div');
        div.className = 'tolov-item';
        div.textContent = `👤 ${item['Bola ismi']} | ${item['Summa']} so'm | ${item['Sana']}`;
        royxatDiv.appendChild(div);
    });
}

yangilash();
