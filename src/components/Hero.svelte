<script>
    import { onMount, onDestroy } from "svelte";
  
    let isVisible = false;
    let divClass = ""; // Class to handle visibility
  
    // Run only in the browser after mount
    onMount(() => {
      // Add scroll listener only on the client-side
      const handleScroll = () => {
        if (window.scrollY >= window.innerHeight) {
          isVisible = true;
        } else {
          isVisible = false;
        }
      };
  
      window.addEventListener("scroll", handleScroll);
  
      // Clean up on destroy
      onDestroy(() => {
        window.removeEventListener("scroll", handleScroll);
      });
    });
  
    // Close button to hide the div with hidden class
    const closeDiv = () => {
      divClass = "hidden";
    };
  
    // Handle button click (optional - Add any behavior if needed)
    const handleBuyTicket = () => {
      alert("Redirecting to ticket purchase page...");
    };
  </script>
  
  <style>
    .bottom-div {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      width: 75%; /* Same as w-3/4 */
      background-color: #ff6600;
      color: white;
      padding: 16px 32px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 9999;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transition: opacity 0.3s ease-in-out, transform 0.3s ease-in-out;
    }
  
    .content-container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
    }
  
    .text-container h1 {
      font-size: 24px;
      font-weight: bold;
      margin-bottom: 8px;
    }
  
    .btn-container {
      display: flex;
      gap: 12px;
      align-items: center;
    }
  
    .buy-btn {
      background-color: white;
      color: #ff6600;
      padding: 12px 24px;
      border-radius: 8px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      border: none;
      transition: background-color 0.3s ease;
    }
  
    .buy-btn:hover {
      background-color: #ffd1b3;
    }
  
    .close-btn {
      background: none;
      border: none;
      font-size: 18px;
      cursor: pointer;
      color: white;
    }
  
    .hidden {
      display: none !important;
    }
  
    .vl-btn6 {
      display: inline-flex;
      align-items: center;
      background-color: white;
      color: #ff6600;
      padding: 12px 24px;
      border-radius: 8px;
      font-size: 16px;
      font-weight: bold;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    .vl-btn6:hover {
      background-color: #ffd1b3;
    }
  
    .vl-btn6 img {
      margin-left: 8px;
    }
  </style>
  
  {#if isVisible}
    <div class="bottom-div {divClass}">
      <div class="content-container">
        <!-- Left Content (Text & Button) -->
       
        <div class="text-container">
            <h1>#10YearsofKSUM</h1>
        </div>
        <div>
            <h1 class=" text-xl">Join us in Building a Sustainable Tomorrow</h1>
        </div>
      
       
        <!-- Right Content (Buy Button & Close Icon) -->
        <div class="btn-container">
          <a class="buy-btn" >BUY A TICKET →</a>
          <button class="close-btn top-0 right-0 font-extralight" on:click={closeDiv}>✖</button>
        </div>
      </div>
    </div>
  {/if}
  