# AgentWarden SDK

Security and permission management for AI Agents.

## Installation
```bash
pip install agentwarden
```

## Quick Start
```python
from agentwarden import AgentWarden

# Initialize with your API key
guard = AgentWarden(api_key="your-api-key")

# Check if agent can execute an action
result = guard.check(
    agent_id="agent-001",
    action="stripe.refund",
    context={"amount": 50}
)

if result.allowed:
    # Execute your action
    stripe.refund.create(amount=50)

    # Log the action
    guard.log("agent-001", "stripe.refund", "success")
else:
    print(f"Action blocked: {result.reason}")
```

## Helper Method
```python
def refund_payment():
    return stripe.refund.create(amount=50)

# Check, execute, and log automatically
result = guard.execute(
    "agent-001",
    "stripe.refund",
    refund_payment,
    context={"amount": 50}
)
```

## Documentation

Visit [https://agentwarden.io](https://agentwarden.io) for full documentation.

## License

MIT License
