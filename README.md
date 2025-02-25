javascript:(function() {
    function randomString(length) {
        const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
        return Array.from({ length }, () => chars[Math.floor(Math.random() * chars.length)]).join("");
    }

    function createGUI(username, password) {
        let gui = document.getElementById("accountGUI");
        if (!gui) {
            gui = document.createElement("div");
            gui.id = "accountGUI";
            gui.style.position = "fixed";
            gui.style.top = "10px";
            gui.style.right = "10px";
            gui.style.background = "rgba(0,0,0,0.8)";
            gui.style.color = "white";
            gui.style.padding = "10px";
            gui.style.borderRadius = "10px";
            gui.style.zIndex = "9999";
            gui.style.fontFamily = "Arial, sans-serif";
            gui.style.width = "250px";
            document.body.appendChild(gui);
        }
        gui.innerHTML = `<strong>Generated Credentials:</strong><br>Username: <br><input type="text" value="${username}" readonly style="width: 100%;"><br>Password: <br><input type="text" value="${password}" readonly style="width: 100%;"><br><button id="regenerateBtn" style="margin-top: 10px;">Generate New</button>`;
        document.getElementById("regenerateBtn").onclick = () => {
            gui.remove();
            startProcess();
        };
    }

    function startProcess() {
        const username = randomString(20);
        const password = randomString(20);
        
        document.querySelector("input[name='birthdayDay']").value = "1";
        document.querySelector("select[name='birthdayMonth']").value = "Jan";
        document.querySelector("input[name='birthdayYear']").value = "2000";
        document.querySelector("input[name='username']").value = username;
        document.querySelector("input[name='password']").value = password;
        document.querySelector("input[value='Male']").click(); // Select Male
        createGUI(username, password);
    }

    function logoutAndRefill() {
        let logoutBtn = document.querySelector("button[aria-label='Log Out']");
        if (logoutBtn) {
            logoutBtn.click();
            setTimeout(startProcess, 3000);
        }
    }

    startProcess();
})();
