    <script src="script.js">
    openai.init({
    application: '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'
});
const form = document.getElementById('performance-statement-form');
form.addEventListener('submit', (event) => {
    event.preventDefault();

    const statement = document.getElementById('performance-statement').value;

    openai.prompt({
        model: 'text-davinci-002',
        prompt: statement,
        temperature: 0.5,
        max_tokens: 115,
        top_p: 1,
        frequency_penalty: 0,
        presence_penalty: 0
    }).then((response) => {
        // Add the shortened performance statement to the appropriate category
        openai.complete({
            model: 'text-davinci-002',
            prompt: response.choices[0].text,
            temperature: 0.5,
            max_tokens: 20,
            top_p: 1,
            frequency_penalty: 0,
            presence_penalty: 0
        }).then((completion) => {
            // Add the generated text to the appropriate category
        });
    });
});
    </script>
