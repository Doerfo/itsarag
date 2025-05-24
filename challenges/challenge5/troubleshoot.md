## Cannot Connect to Azure SQL Database from Codespace

If you encounter connection errors when accessing your Azure SQL Database from your Codespace, you may need to add your Codespace's public IP address to the Azure SQL Server firewall.

### Step 1: Retrieve Your Codespace Public IP

Open the integrated terminal in your Codespace and run:

```bash
curl ifconfig.me
```

Copy the IP address that is returned.

### Step 2: Add the IP Address to Azure SQL Server Firewall

1. Go to the [Azure Portal](https://portal.azure.com/).
2. Navigate to your SQL Server resource (not the database, but the server).
3. Under **Networking** or **Firewalls and virtual networks**, click **Add client IP** or manually add the IP you copied.
4. Save the changes.

**Note:**  
It may take a few minutes for the firewall rule to take effect.

### Step 3: Retry Your Connection

Try connecting to your Azure SQL Database again from your Codespace. If you still encounter issues, double-check that the IP address is correct and that you are using the right connection string and credentials.

---

## Known Issue: Stock Agent Crashes on Certain Questions

**Problem:**  
When running the multi-agent workflow, question index 7 from `challenge5.ipynb` (`"Can you buy 10 shares of APPLE for me?"`) will cause the stock agent to crash with an `OutputParserException`.

**Reason:**  
The SQL Agent expects the LLM to return a specific action/format for tool use, but for unsupported actions (like buying shares), the LLM returns a plain text answer (e.g., "I cannot perform transactions or buy shares for you..."). This output cannot be parsed by the agent, resulting in an error.


---

## Known Issue: AzureAISearchRetriever May Fail Due to Missing Service Name

**Problem:**  
The following code for creating a retriever may not work as expected:
```python
retriever = AzureAISearchRetriever(
    api_key=AZURE_SEARCH_API_KEY,
    service_name=AZURE_SEARCH_ENDPOINT,
    index_name=AZURE_SEARCH_INDEX,
    top_k=20
)
```

**Reason:**  
The environment variable `AZURE_SEARCH_SERVICE` is missing in the retriever initialization. The correct parameter should be `service_name=AZURE_SEARCH_SERVICE`, not `AZURE_SEARCH_ENDPOINT`.

**Solution:**  
Make sure to add the following to your environment variable setup:
```python
AZURE_SEARCH_SERVICE = os.getenv("AZURE_SEARCH_SERVICE")
```
And update the retriever initialization to:
```python
retriever = AzureAISearchRetriever(
    api_key=AZURE_SEARCH_API_KEY,
    service_name=AZURE_SEARCH_SERVICE,
    index_name=AZURE_SEARCH_INDEX,
    top_k=20
)
```

