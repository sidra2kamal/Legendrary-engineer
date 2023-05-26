# Legendrary-engineer
import unittest
from engine import Engine
from battery import Battery

class EngineTests(unittest.TestCase):
    def test_engine_start(self):
        engine = Engine()
        self.assertFalse(engine.is_running())
        engine.start()
        self.assertTrue(engine.is_running())

    def test_engine_stop(self):
        engine = Engine()
        engine.start()
        self.assertTrue(engine.is_running())
        engine.stop()
        self.assertFalse(engine.is_running())

class BatteryTests(unittest.TestCase):
    def test_battery_charge(self):
        battery = Battery()
        self.assertEqual(battery.get_charge_level(), 0)
        battery.charge(50)
        self.assertEqual(battery.get_charge_level(), 50)
        battery.charge(25)
        self.assertEqual(battery.get_charge_level(), 75)

    def test_battery_discharge(self):
        battery = Battery()
        battery.charge(100)
        self.assertEqual(battery.get_charge_level(), 100)
        battery.discharge(50)
        self.assertEqual(battery.get_charge_level(), 50)
        battery.discharge(25)
        self.assertEqual(battery.get_charge_level(), 25)

class CarFactory:
    @staticmethod
    def check_tire_wear(tire_wear):
        tire_wear_sum = sum(tire_wear)
        if tire_wear_sum >= 3:
            return True
        return False

class Engine:
    def __init__(self):
        self.running = False

    def is_running(self):
        return self.running

    def start(self):
        self.running = True

    def stop(self):
        self.running = False

if __name__ == '__main__':
    unittest.main()
