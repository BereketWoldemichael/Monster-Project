class Monster():
    def __init__(self, name, hp=20):
        self.exp = 0
        self.name = name
        self.type = 'Normal'
        self.max_hp = hp
        self.current_hp = self.max_hp
        self.attacks = {'wait': 0}
        self.possible_attacks = {'sneak_attack': 1, 'slash': 2, 'ice_storm': 3, 'fire_storm': 3, 'whirlwind': 3, 'earthquake': 2, 'double_hit': 4, 'tornado': 4, 'wait': 0}




    def add_attack(self, attack_name):
        if attack_name not in self.possible_attacks: # If you try to add an invalid attack return False.
            return False  # Invalid attack
        if len(self.attacks) == 4:  # If you add an attack when the monster already has four, the weakest one should be dropped automatically.
            
            weakest_attack_value = min(self.attacks.values())  # This will get the lowest attack value then I will collect them and if there is a tie pick the one that comes alphabetically
            weakest_at = [attack for attack, value in self.attacks.items() if value == weakest_attack_value]
            attack_remove = sorted(weakest_at)[0]
            del self.attacks[attack_remove]
        self.attacks[attack_name] = self.possible_attacks[attack_name]

        return True  # If adding the attack ended successfully, return True

    def remove_attack(self, attack_name):
    # this checks if it's a valid attack entry
        if attack_name not in self.attacks:
            return False
        del self.attacks[attack_name]
        if not self.attacks:
          self.attacks["wait"] = 0

        return True


if __name__ == '__main__':
    fall = Monster("Demon")
    fall.add_attack("fire_storm")
    fall.add_attack("slash")
    fall.add_attack("tornado")

    fall2 = Monster("food")
    fall2.add_attack("fire_storm")
    fall2.add_attack("slash")
    fall2.add_attack("tornado")





