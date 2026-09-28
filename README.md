# Three-phase-fault-detector
# Three Phase Fault Detector

MAX_CURRENT = 10       # Maximum safe current (A)
MIN_VOLTAGE = 200      # Minimum safe voltage (V)
MAX_VOLTAGE = 250      # Maximum safe voltage (V)

print("================================")
print("   THREE PHASE FAULT DETECTOR")
print("================================")

# Input values
v1 = float(input("Enter Phase R voltage (V): "))
v2 = float(input("Enter Phase Y voltage (V): "))
v3 = float(input("Enter Phase B voltage (V): "))

i1 = float(input("Enter Phase R current (A): "))
i2 = float(input("Enter Phase Y current (A): "))
i3 = float(input("Enter Phase B current (A): "))

fault = False

# Voltage checking
for phase, voltage in [("R", v1), ("Y", v2), ("B", v3)]:
    if voltage < MIN_VOLTAGE:
        print(f"⚠️ Phase {phase}: Under-voltage fault")
        fault = True
    elif voltage > MAX_VOLTAGE:
        print(f"⚠️ Phase {phase}: Over-voltage fault")
        fault = True

# Current checking
for phase, current in [("R", i1), ("Y", i2), ("B", i3)]:
    if current > MAX_CURRENT:
        print(f"⚠️ Phase {phase}: Overcurrent fault")
        fault = True

# Final result
if fault:
    print("\n🔴 THREE-PHASE FAULT DETECTED")
    print("🔌 Protection system activated")
    print("⚙️ Motor/Load should be disconnected")
else:
    print("\n🟢 THREE-PHASE SYSTEM NORMAL")
    print("✅ No fault detected")
    print("⚡ Load can continue operating")
