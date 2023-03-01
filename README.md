# some-practice
here I have paste my practice work on python

# working on dictonary 
from typing import Final

MAX_FLYING_WEIGHT: Final[float]=15

def can_fly(weight: float) -> bool:

    return weight <= MAX_FLYING_WEIGHT

def calc_weight(weight: float) -> float:
    return (weight +32)/8

def flying_friends(friends: dict[str,float]) -> None:

    for name,earth_weight in friends.items():
        zortan_weight = calc_weight(earth_weight)
        if can_fly(zortan_weight):
            print(f"{name}: {zortan_weight} kgs can fly on zortan!")
        else:
            print(f"{name}: {zortan_weight} kgs can only walks on Zortan!")

def main() -> None:
    friends: dict[str, float]={ "cece":54,"Roko": 88,"chiko": 50,"Niko":102,"Ziko": 90}
    flying_friends(friends)

main()

# END :.............................................................
 
# GAME IN FUNCTIONS



from typing import Final
from random import randint

character = dict[str, str | int]

def get_all_superheros() -> list[character]:

    IRONMAN: [character] = {"name": "Ironman", "attack_power": 250, "life": 1000}
    BLACKWIDOW: [character] = {"name": "BLACKWIDOW", "attack_power": 180, "life": 800}
    SPIDERMAN: [character] = {"name": "SPIDERMAN", "attack_power": 190, "life": 700}
    HULK: [character] = {"name": "HULK", "attack_power": 300, "life": 1100}
    superheros: list[character] = [IRONMAN, BLACKWIDOW, SPIDERMAN, HULK]
    return superheros

def get_superhero(index: int) -> character | None:
    superheros = get_all_superheros()
    if index < len(superheros):
        return superheros[index]
    else:
        return None

def get_all_villains() -> list[character]:
    # SUPER VILLAINS
    THANOS: Final[character] = {"name": "Thanos", "attack_power": 250, "life": 1500}
    REDSKULL: [character] = {"name": "redskull", "attack_power": 300, "life": 800}
    PROXIMA: [character] = {"name": "proxima", "attack_power": 320, "life": 800}
    villains: list[character] = [THANOS, REDSKULL, PROXIMA]
    return villains

def get_villain(index: int) -> character | None:
    villains = get_all_villains()
    if index < len(villains):
        return villains[index]
    else:
        return None



hero_life=0
villain_life=0


def inc_hero_life(life: int) -> None:
    global hero_life
    hero_life += life

def dec_hero_life(life: int) -> None:
    global hero_life
    hero_life -= life

def inc_villain_life(life: int) -> None:
    global villain_life
    villain_life += life

def dec_villain_life(life: int) -> None:
    global villain_life
    villain_life -= life


def attack() -> None:

    for attack_num in range(3):
        hero_index = randint(0, 3)
        villain_index = randint(0, 2)
        current_superhero = get_superhero(hero_index)
        current_villain = get_villain(villain_index)

        if current_superhero and current_villain:
            simulate_attack(attack_num,current_villain,current_superhero)
        else:
            print(f"Error! NO superhero or villains to fight")


def simulate_attack(attack_num: int, villain: character, superhero: character) -> None:
    # hero life
    inc_hero_life(superhero["life"])
    inc_villain_life(villain["life"])

    print(
        f"Attack : {attack_num + 1} => {superhero['name']} is going to fight with : {villain['name']}")

    # attack
    dec_hero_life(villain['attack_power'])
    dec_villain_life(superhero['attack_power'])

    #print a nice separating line
    print("=" * 58)

def win_or_loose() -> None:
    # win or loss
    WIN_MSG: Final[str] = "you successful save zortan!!!! ***"
    LOST_MST: Final[str] = "Thanos killed Avengers and captured Zortan!!!"
    if hero_life >= villain_life:
        print("hero life is :", hero_life)
        print("villain life is : ", villain_life)
        print(WIN_MSG)
    else:
        print("hero life is :", hero_life)
        print("villain life is : ", villain_life)
        print(LOST_MST)

def main() -> None:
    attack()
    win_or_loose()

main()


# END :.......................................................................................................->>>
