function filterJSON(jsonData, filters) {
  return jsonData.filter(function(item) {
    // Inicialmente, nenhum dos filtros é correspondido
    let matches = false;
    // Itera sobre cada filtro definido
    for (let prop in filters) {
      // Verifica se o filtro atual está definido para este item do JSON
      if (item.hasOwnProperty(prop)) {
        // Recupera o valor do item JSON atual para o campo correspondente
        let fieldValue = item[prop];
        // Recupera o valor do filtro atual para o campo correspondente
        let filterValue = filters[prop];
        // Verifica se a condição definida no filtro atual é correspondida para este campo do item JSON
        if (typeof filterValue === 'object' && filterValue !== null) {
          // O valor do filtro é um objeto contendo um operador de comparação e um valor de comparação
          let operator = Object.keys(filterValue)[0];
          let compareValue = filterValue[operator];
          switch (operator) {
            case '>':
              matches = (fieldValue > compareValue);
              break;
            case '>=':
              matches = (fieldValue >= compareValue);
              break;
            case '=':
              matches = (fieldValue === compareValue);
              break;
            case '<=':
              matches = (fieldValue <= compareValue);
              break;
            case '<':
              matches = (fieldValue < compareValue);
              break;
            default:
              matches = false;
          }
        } else {
          // A condição é definida como um valor a ser comparado diretamente com o valor do campo
          matches = (fieldValue === filterValue);
        }
        // Se a condição não for correspondida, pare de iterar sobre os outros filtros
        if (!matches) {
          break;
        }
      }
    }
    // Retorna verdadeiro se todos os filtros forem correspondidos, senão retorna falso
    return matches;
  });
}

let jsonData = [
  {name: 'John', age: 35, city: 'New York'},
  {name: 'Sarah', age: 28, city: 'Los Angeles'},
  {name: 'Mike', age: 42, city: 'Chicago'},
  {name: 'Linda', age: 30, city: 'New York'}
];

let filters = {age: { '>=': 30 }};
let filteredData = filterJSON(jsonData, filters);
console.log(filteredData);

filters = {name: 'John', city: 'New York'};
filteredData = filterJSON(jsonData, filters);
console.log(filteredData);
