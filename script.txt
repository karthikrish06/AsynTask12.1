// Function to fetch data using promises
function fetchData(url) {
    return new Promise((resolve, reject) => {
        fetch(url)
            .then(response => {
                if (!response.ok) {
                    throw new Error(`Network response was not ok: ${response.status}`);
                }
                return response.json();
            })
            .then(data => resolve(data))
            .catch(error => reject(error));
    });
}

// Function to update the dog image
function updateDogImage() {
    fetchData('https://dog.ceo/api/breeds/image/random')
        .then(data => {
            document.getElementById('dogImage').src = data.message;
        })
        .catch(error => console.error(error));
}