<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name:   SHRI LEKSHMAN RIKHESH R       </h3>
<h3>Register Number:   212224060249     </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>


<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

<h2>Program:</h2>

```
import random
import string

def fitness(candidate, target):
    return sum(abs(ord(candidate[i]) - ord(target[i])) for i in range(len(target)))

def mutate(parent):
    idx = random.randrange(len(parent))
    new_char = random.choice(string.printable[:95])
    return parent[:idx] + new_char + parent[idx + 1:]

def hill_climb(target):
    current = ''.join(random.choice(string.printable[:95]) for _ in range(len(target)))
    current_score = fitness(current, target)
    while True:
        neighbor = mutate(current)
        neighbor_score = fitness(neighbor, target)
        if neighbor_score <= current_score:
            current, current_score = neighbor, neighbor_score
            print(f"Score: {current_score} Solution : {current}")
        if current_score == 0:
            break
    return current

target_string = "Artificial Intelligence"
solution = hill_climb(target_string)
print("\nFinal Solution:", solution)

```

<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Output:</h2>
Score: 687 Solution : 7hD}&)MHd63^JyqG0pea*D,
Score: 641 Solution : 7hD}&{MHd63^JyqG0pea*D,
Score: 635 Solution : 7vD}&{MHd63^JyqG0pea*D,
Score: 606 Solution : 7vD}C{MHd63^JyqG0pea*D,
Score: 585 Solution : 7vD}C{M]d63^JyqG0pea*D,
Score: 576 Solution : 7vD}C{Mld63^JyqG0pea*D,
Score: 530 Solution : 7vr}C{Mld63^JyqG0pea*D,
Score: 516 Solution : 7vr}C{Mld63^JyqG0pea*t,
Score: 508 Solution : 7vruC{Mld63^JyqG0pea*t,
Score: 494 Solution : 7vruCeMld63^JyqG0pea*t,
Score: 480 Solution : 7vruQeMld63^JyqG0pea*t,
Score: 480 Solution : 7vru{eMld63^JyqG0pea*t,
Score: 449 Solution : 7vru{eMld63^JyqG0pea*tK
Score: 448 Solution : 7vuu{eMld63^JyqG0pea*tK
Score: 442 Solution : 7vuu{eMld63^JyqM0pea*tK
Score: 414 Solution : 7vuu{eMld63^vyqM0pea*tK
Score: 409 Solution : 7vuu{eMld;3^vyqM0pea*tK
Score: 408 Solution : 7vuu{eMld;3^vyqM0peh*tK
Score: 405 Solution : 7vuu{eMld;3[vyqM0peh*tK
Score: 393 Solution : 7vuu{eMld;3OvyqM0peh*tK
Score: 391 Solution : 7vuu{eMld;3OvyqM0deh*tK
Score: 379 Solution : 7vuu{eMld;3OvyqM<deh*tK
Score: 363 Solution : 7vuu{e]ld;3OvyqM<deh*tK
Score: 325 Solution : 7vuu{e]lda3OvyqM<deh*tK
Score: 325 Solution : 7vuu{e]fda3OvyqM<deh*tK
Score: 320 Solution : 7vuu{e]fda3OvylM<deh*tK
Score: 308 Solution : 7vuu{e]fda3OvylM<deh*^K
Score: 292 Solution : 7vuuae]fda3OvylM<deh*^K
Score: 283 Solution : 7vuuae]fda*OvylM<deh*^K
Score: 231 Solution : 7vuuae]fda*OvylM<deh^^K
Score: 227 Solution : 7vuuae]fda*OvylM<dehz^K
Score: 180 Solution : 7vuuae]fda*OvylMmdehz^K
Score: 176 Solution : 7vuuae]fds*OvylMmdehz^K
Score: 146 Solution : 7vuuae]fds*Ovylmmdehz^K
Score: 138 Solution : 7vuuae]fds*Ovylmmdehz^w
Score: 134 Solution : 7vuuae]fds*Ovslmmdehz^w
Score: 128 Solution : Evuuae]fds*Ovslmmdehz^w
Score: 128 Solution : Evuuae]fds*Ovulmmdehz^w
Score: 124 Solution : Evuuae]fds*Ovulmmdehzdw
Score: 114 Solution : Evuuae]fds*Ovulmmdehzd]
Score: 113 Solution : Evuuae]fds*Ovulmmmehzd]
Score: 111 Solution : Evuuae]fds*Otulmmmehzd]
Score: 111 Solution : Evsuae]fds*Otulmmmehzd]
Score: 106 Solution : Evsuae]fds*Jtulmmmehzd]
Score: 101 Solution : Evsuae]fds*Jtucmmmehzd]
Score: 98 Solution : Evsuaj]fds*Jtucmmmehzd]
Score: 92 Solution : Evsuajcfds*Jtucmmmehzd]
Score: 90 Solution : Evsuajcfds*Jtucmmmghzd]
Score: 87 Solution : Evsuajcfds*Jtucmmmghzd`
Score: 77 Solution : Evsgajcfds*Jtucmmmghzd`
Score: 74 Solution : Evsgajcids*Jtucmmmghzd`
Score: 71 Solution : Evsgajcias*Jtucmmmghzd`
Score: 68 Solution : @vsgajcias*Jtucmmmghzd`
Score: 66 Solution : @vsgijcias*Jtucmmmghzd`
Score: 66 Solution : Bvsgijcias*Jtucmmmghzd`
Score: 61 Solution : Bvsgijcias*Jtucmmmghgd`
Score: 61 Solution : Bvsgijcias*Jtugmmmghgd`
Score: 61 Solution : Bvsgijcias*Jtugmmmghgd`
Score: 57 Solution : Bvsgijcias*Jtugmmmghkd`
Score: 57 Solution : Bvsgijcias*Jtugkmmghkd`
Score: 52 Solution : Bvsgijciaj*Jtugkmmghkd`
Score: 49 Solution : Bvsgijciaj*Jtugkmhghkd`
Score: 45 Solution : Brsgijciaj*Jtugkmhghkd`
Score: 42 Solution : Brsgijciaj'Jtugkmhghkd`
Score: 41 Solution : Brsgijciaj'Jtudkmhghkd`
Score: 41 Solution : Brsgijciaj'Jtudkmhgbkd`
Score: 41 Solution : Brskijciaj'Jtudkmhgbkd`
Score: 36 Solution : Brskijciaj'Joudkmhgbkd`
Score: 36 Solution : Brskcjciaj'Joudkmhgbkd`
Score: 35 Solution : Brskcjciaj'Jouekmhgbkd`
Score: 33 Solution : Brskcjciaj'Jouekmhgbod`
Score: 31 Solution : Brskcjciaj'Jouekmhgfod`
Score: 28 Solution : Brskfjciaj'Jouekmhgfod`
Score: 23 Solution : Brskfjciaj'Jouekmhgfode
Score: 23 Solution : Brskfjciaj'Jouekmhgfode
Score: 23 Solution : Brskfjciaj'Jouemmhgfode
Score: 23 Solution : Brskfjcian'Jouemmhgfode
Score: 23 Solution : Brskfjcian'Jouemmjgfode
Score: 21 Solution : Brsifjcian'Jouemmjgfode
Score: 20 Solution : Brsifjcian'Jouelmjgfode
Score: 20 Solution : Brsifhcian'Jouelmjgfode
Score: 20 Solution : Brsifhcian'Jouelmjgfode
Score: 17 Solution : Brsifhcian$Jouelmjgfode
Score: 16 Solution : Brsifhcian$Jouelmjgfoce
Score: 16 Solution : Brsifhcian$Jouelmjgfoce
Score: 16 Solution : Brsifhcian$Jouelmjgdoce
Score: 16 Solution : Brsifhcian$Jouelmjgdoce
Score: 15 Solution : Brtifhcian$Jouelmjgdoce
Score: 15 Solution : Brtifhcian$Jouelmjgdoce
Score: 15 Solution : Brtifhcian$Jouelmjgdoce
Score: 15 Solution : Brtifhcian$Jouelmjgdoce
Score: 15 Solution : Brtifhcian$Jouelmjgdoce
Score: 15 Solution : Brtifhcian$Jouelmjgdoce
Score: 14 Solution : Brtifhcian$Jnuelmjgdoce
Score: 14 Solution : Brtifhcian$Jnuelmjgdoce
Score: 13 Solution : Artifhcian$Jnuelmjgdoce
Score: 13 Solution : Artifhcian$Jnuelmjgdoce
Score: 13 Solution : Artifhcian$Jnuelmjgdoce
Score: 12 Solution : Artifhcian#Jnuelmjgdoce
Score: 11 Solution : Artifhcian#Inuelmjgdoce
Score: 10 Solution : Artifhcian#Inuelljgdoce
Score: 10 Solution : Artifhcian#Inuelljgdoce
Score: 10 Solution : Artifhcian#Inuelljgdoce
Score: 10 Solution : Artifhciaj#Inuelljgdoce
Score: 10 Solution : Artifhciaj#Inuelljgdoce
Score: 9 Solution : Artifhciak#Inuelljgdoce
Score: 8 Solution : Artificiak#Inuelljgdoce
Score: 8 Solution : Artificiak#Inuelljgdoce
Score: 8 Solution : Artificiam#Inuelljgdoce
Score: 8 Solution : Artificiam#Inuelljgdoce
Score: 8 Solution : Artificiam#Inselljgdoce
Score: 8 Solution : Artificiam#Inselljgdmce
Score: 8 Solution : Artificiak#Inselljgdmce
Score: 7 Solution : Artificial#Inselljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 7 Solution : Artificial#Inuelljgdmce
Score: 6 Solution : Artificial"Inuelljgdmce
Score: 6 Solution : Artificial"Inuelljgdmce
Score: 6 Solution : Artificial"Inuelljgdmce
Score: 4 Solution : Artificial Inuelljgdmce
Score: 4 Solution : Artificial Inuellhgdmce
Score: 4 Solution : Artificial Inuellhgdmce
Score: 3 Solution : Artificial Inuellhgdnce
Score: 3 Solution : Artificial Inuellhgdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 2 Solution : Artificial Inuelligdnce
Score: 1 Solution : Artificial Inuelligence
Score: 1 Solution : Artificial Inuelligence
Score: 1 Solution : Artificial Inuelligence
Score: 1 Solution : Artificial Inuelligence
Score: 1 Solution : Artificial Inuelligence
Score: 1 Solution : Artificial Inuelligence
Score: 1 Solution : Artificial Inuelligence
Score: 0 Solution : Artificial Intelligence

Final Solution: Artificial Intelligence


<h2>Output</h2>

<img width="486" height="1068" alt="image" src="https://github.com/user-attachments/assets/062c80a7-ab1b-42cb-90d7-7e1dc3c24c2c" />


<h2>Result</h2>

Thus, the Simple Hill Climbing Algorithm was implemented and a string was generated by mutating a single character at each iteration successfully.
