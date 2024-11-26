function getColors() {
    const colorTableDiv = document.querySelector('#colornamestable');
    
    if (!colorTableDiv) {
        console.error("Tabela de cores não encontrada na página.");
        return;
    }

    const colors = [];


    colorTableDiv.querySelectorAll('div, span').forEach(function(col) {
        let colorName = col.textContent.trim(); 
        if (colorName && colorName.toLowerCase() !== colorName) { // 
            colors.push(colorName.toLowerCase());
        }
    })

    console.log(colors) 
    return colors 
}

function selectRandomColors(n, colors) {
    const selectedColors = []
    
 
    const colorsCopy = [...colors];


    for (let i = 0; i < n; i++) {
        const randomIndex = Math.floor(Math.random() * colorsCopy.length); 
        selectedColors.push(colorsCopy.splice(randomIndex, 1)[0]); // 
    }
    
    return selectedColors
}


function chooseRandomColor(colors) {
    
    const randomColor = colors[Math.floor(Math.random() * colors.length)];
    console.log("Cor Aleatória Escolhida: " + randomColor) 
}


document.addEventListener('DOMContentLoaded', function() {
    setTimeout(function() {
        const colors = getColors() 

        if (colors && colors.length > 0) {
            
            const randomColors = selectRandomColors(10, colors);

            
            console.log("10 Cores Aleatórias: ", randomColors.join(", "))
            
            
            chooseRandomColor(randomColors);
        }
    }, 1000) 
})
