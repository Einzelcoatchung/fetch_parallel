# fetch_parallel

```

const fetchDataParallelOneResponse = () => {
  console.log("PARALLEL fetch")

  console.log("Starting to fetch todos...")
  
  const promFetches = []

  promFetches.push( fetch("https://jsonplaceholder.typicode.com/todos") )
  promFetches.push( fetch("https://jsonplaceholder.typicode.com/users") )

  Promise.all(promFetches)
  .then(responses => {
    const promData = []
    // loop over 
    responses.forEach(resp => {
      promData.push( resp.json() )
    })
    // await all JSON parsings to finish
    return Promise.all(promData)
  })
  .then(dataAll => {
    console.log(dataAll)
  })
}


// AXIOS
const fetchDataParallelOneResponse = () => {
  console.log("PARALLEL fetch")

  console.log("Starting to fetch todos...")
  
  const promFetches = []

  promFetches.push( axios.get("https://jsonplaceholder.typicode.com/todos") )
  promFetches.push( axios.get("https://jsonplaceholder.typicode.com/users") )

  Promise.all(promFetches)
  .then(responses => {
     const dataAll = responses.map( resp => resp.data ) 
     res.send( dataAll )
  })
}
```
