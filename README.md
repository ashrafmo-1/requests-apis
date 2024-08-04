# requests apis

Foobar is a Python library for dealing with word pluralization.

## method "GET" data

using fetch in this example

```javascript
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data))
      .catch(error => setError(error));
  }, []);

  if (error) return <div>Error: {error.message}</div>;
  if (!data) return <div>Loading...</div>;
```

## using axios in this example

```javascript
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get('https://api.example.com/data')
      .then(response => {
          setData(response.data);
          console.log(response.data);
       }
)
      .catch(error => setError(error));
  }, []);

  if (error) return <div>Error: {error.message}</div>;
  if (!data) return <div>Loading...</div>;
```

## using react-query in this example

install
```bach
npm install react-query
```
```javascript
const fetchData = async () => {
  const { data } = await axios.get('https://api.example.com/data');
  return data;
};

const ReactQueryExample = () => {
  const { data, error, isLoading } = useQuery('fetchData', fetchData);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
```


## method "POST" data

using fetch in this example
```javascript
const [data, setData] = useState(null);
const [error, setError] = useState(null);

const postData = async () => {
  try {
    const response = await fetch('https://api.example.com/data', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ key: 'value' }), // Adjust the payload as needed
    });
    const result = await response.json();
    setData(result);
  } catch (error) {
    setError(error);
  }
};

useEffect(() => {
  postData();
}, []);

if (error) return <div>Error: {error.message}</div>;
if (!data) return <div>Loading...</div>;
```


using axios in this example

```javascript
const [data, setData] = useState(null);
const [error, setError] = useState(null);

useEffect(() => {
  axios.post('https://api.example.com/data', { key: 'value' }) // Adjust the payload as needed
    .then(response => {
      setData(response.data);
      console.log(response.data);
    })
    .catch(error => setError(error));
}, []);

if (error) return <div>Error: {error.message}</div>;
if (!data) return <div>Loading...</div>;
```

Using react-query in this example

```javascript
const postData = async () => {
  const { data } = await axios.post('https://api.example.com/data', { key: 'value' }); // Adjust the payload as needed
  return data;
};

const ReactQueryPostExample = () => {
  const { data, error, isLoading } = useQuery('postData', postData);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
  return <div>Data: {JSON.stringify(data)}</div>;
};

```



## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate

## License

[MIT](https://choosealicense.com/licenses/mit/)
