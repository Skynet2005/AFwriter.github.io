<!DOCTYPE html>
<html>
<head>
    <title>Performance Statements</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
    <script src="https://cdn.jsdelivr.net/npm/@openai/openai@latest/dist/openai.min.js"></script>
</head>
<body>
    <form>
        <label>Performance Statement:</label>
        <input type="text" id="performance-statement">
        <input type="submit" value="Submit">
    </form>
    <div id="categories">
        <div id="leadership-primary-duties">
            <h2>Leadership & Primary Duties</h2>
            <ul id="statements-list">
                <!-- Performance statements for this category will be added here dynamically using JavaScript -->
            </ul>
        </div>
        <div id="whole-airman-concept">
            <h2>Whole Airman Concept</h2>
            <ul id="statements-list">
                <!-- Performance statements for this category will be added here dynamically using JavaScript -->
            </ul>
        </div>
        <div id="rater-additional-rater-comments">
            <h2>Rater/Additional Rater Comments</h2>
            <ul id="statements-list">
                <!-- Performance statements for this category will be added here dynamically using JavaScript -->
            </ul>
        </div>
    </div>
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
</body>
</html>
