
## "Test and set", "exchange " i "compare and swap" funkcije

Ove funkcije su atomicne i tretiraju se kao hardverske instrukcije, napravljene su bas iz razloga da za izvrsenje tih instrukcija **nije potreban kernel mod** i da **proces ostaje u running stanju nakon izvrsenja tih funkcija**

Njihova primena je sto se koriste za sinhronizaciju niti ali na hardverskom nivou, mada ovo nije efikasno resenje.