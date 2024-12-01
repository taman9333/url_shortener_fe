<script>
  let url = ""; // URL input by the user
  let shortenedCode = ""; // Shortened URL code returned by the server
  let shortenedUrl = ""; // Full Shortened URL
  let error = ""; // Error message if something goes wrong

  const shortenUrl = async (e) => {
    e.preventDefault();
    // Clear previous results
    error = "";
    shortenedCode = "";
    shortenedUrl = "";

    try {
      const response = await fetch('http://localhost:9292/shorten', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ url })
      });

      if (!response.ok) {
        throw new Error(await response.text());
      }

      const data = await response.json();
			shortenedCode = data.short_url
			shortenedUrl = `http://localhost:9292/${data.short_url}`;
    } catch (err) {
      error = `Error: ${err.message}`;
    }
  };
</script>

<main>
  <h1>URL Shortener</h1>

  <form on:submit={shortenUrl}>
    <label for="url">Enter URL:</label>
    <input
      type="url"
      id="url"
      bind:value={url}
      required
      placeholder="https://test.com"
      style="margin-left: 10px; padding: 5px; width: 300px;"
    />
    <button type="submit" style="margin-left: 10px; padding: 5px 15px;">
      Shorten
    </button>
  </form>

  {#if shortenedCode}
    <p style="margin-top: 20px;">
      Your shortened URL: <a href={shortenedUrl}>{shortenedCode}</a>
    </p>
  {/if}

  {#if error}
    <p style="margin-top: 20px; color: red;">{error}</p>
  {/if}
</main>

<style>
  main {
    font-family: Arial, sans-serif;
    padding: 20px;
  }

  label {
    font-weight: bold;
  }
</style>