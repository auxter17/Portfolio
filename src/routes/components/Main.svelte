<script>
    let reminderText = "";
    const webhookUrl = "https://discord.com/api/webhooks/1249573774853013590/eUgsURxpS85JUTHrCA_9e0gyrGlSeAqoRY8Y4E8x9CrSC2PSZm-YTrWZQZFR8io0sPas";
  
    // Function to send the reminder message
    async function sendToDiscord(text) {
      try {
        const response = await fetch(webhookUrl, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            content: `Good day sir angelo, Daily reminder: ${text}`
          })
        });
  
        if (!response.ok) {
          throw new Error("Network response was not ok");
        }
  
        console.log("Message sent successfully!");
      } catch (error) {
        console.error("Failed to send message:", error);
      }
    }
  
    // Function to send the reminder message every 30 seconds (for debugging purposes)
    async function sendDailyReminder() {
      if (reminderText) {
        await sendToDiscord(reminderText);
      }
    }
  
    // Schedule the function to run every 30 seconds (for debugging purposes)
    setInterval(sendDailyReminder, 30000); // Run every 30 seconds
  </script>
  
  <div class="flex justify-center p-10">
    <div class="flex gap-x-10 w-full">
      <div class="flex justify-center bg-gray-500 w-full h-[470px] rounded">
        <h1>Content 1</h1>
      </div>
      <div class="justify-center w-full h-[470px] rounded">
        <div class="flex justify-center p-2">
          <h5 class="font-bold">Make an auto reminder in your Discord here!</h5>
        </div>
        <div class="flex gap-x-2 justify-center">
          <input
            type="text"
            placeholder="Enter a text for the reminder"
            class="h-[50px] w-[270px] p-2 rounded"
            bind:value={reminderText}
          />
          <button on:click={sendToDiscord(reminderText)} class="h-[48px] bg-gray-500 p-2 rounded">Save</button>
        </div>
      </div>
    </div>
  </div>
  