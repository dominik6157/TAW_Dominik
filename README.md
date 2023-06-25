# Projekt zaliczeniowy z TAW

## Opis 
Warunkiem zaliczenia jest przygotowanie aplikacji serwerowej opartej o REST API oraz raportu komunikacji z tym serwerem według podanego scenariusza.
Raport komunikacji z serwerem powinien zawierać zestawienie wywołanych żądań do serwera wraz z adresem zasobu, metodą http, body żądania, nagłówkami żądania oraz odpowiedzią serwera na wysłane żądanie w postaci kodu odpowiedzi http oraz body odpowiedzi.

Przykładowy opis żądania z ćwiczeń:
```
Metoda: POST
Adres zasobu: http://localhost:8080/api/activities
Nagłówki: Content-Type: application/json
Request Body:
{
"nazwa": "programowanie",
"priorytet": 10
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak
```

W ramach projektu należy przygotować REST API bazujące na zasobie przedmiotów na studia. Każdy przedmiot na studia powinien zawierać informacje o:
- nazwie przedmiotu,
- punktach ects,
- numerze sali, w której odbywają się zajęcia,
- informacji czy przedmiot kończy się egzaminem.

Serwer powinien umożliwiać wprowadzanie nowych przedmiotów, pobieranie przedmiotów oraz usuwanie przedmiotów.
Ocena za zaliczenie będzie uzależniona od złożoności przygotowanego rozwiązania.
W podstawowej wersji serwer powinien umożliwiać wprowadzanie nowego przedmiotu, pobieranie wszystkich przedmiotów i usuwanie wszystkich przedmiotów. W rozszerzonej wersji serwer powinien pozwalać na filtrację pod kątem informacji o tym czy przedmiot kończy się egzaminem oraz o filtrację po numerze sali, w której obywają się zajęcia. Serwer powinien także udostępniać możliwość pobierania konkretnego zasobu w oparciu o identyfikator oraz usuwanie konkretnego przedmiotu w oparciu o identyfikator.

## Scenariusz do raportu
1. Wprowadzenie przedmiotów do systemu w podanej kolejności:
- Nazwa: Metodologie obiektowe, ECTS: 2, Sala: 216, Egzamin: tak,
- Nazwa: Testowanie oprogramowania, ECTS: 1, Sala: 216, Egzamin: nie,
- Nazwa: Technologie i aplikacje webowe, ECTS: 3, Sala: 208, Egzamin: nie,
- Nazwa: Zarządzanie projektem informatycznym, ECTS: 2, Sala: 216, Egzamin: nie,
- Nazwa: Zaawansowane technologie bazodanowe, ECTS: 3, Sala: 208, Egzamin: nie,
- Nazwa: Technologie komponentowe i sieciowe, ECTS: 2, Sala: 208, Egzamin: tak
2. Pobranie wszystkich przedmiotów,
3. Pobranie przedmiotów, które mają egzamin,
4. Pobranie przedmiotów, które odbywają się w sali 216,
5. Pobranie przedmiotów które nie mają egzaminu i odbywają się w sali 208,
6. Pobranie przedmiotu o identyfikatorze 3,
7. Pobranie przedmiotu o identyfikatorze 15,
8. Usunięcie przedmiotu o identyfikatorze 2,
9. Pobranie wszystkich przedmiotów,
10. Usunięcie wszystkich przedmiotów,
11. Pobranie wszystkich przedmiotów.

## 1. Wprowadzenie przedmiotów do systemu w podanej kolejności
```
Metoda: POST
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body:
{
"Nazwa": "Metodologie obiektowe",
"ECTS": 2,
"Sala": 216,
"Egzamin": "tak"
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak

Metoda: POST
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body:
{
"Nazwa": "Testowanie oprogramowania",
"ECTS": 1,
"Sala": 216,
"Egzamin": "nie"
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak

Metoda: POST
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body:
{
"Nazwa": "Technologie i aplikacje webowe",
"ECTS": 3,
"Sala": 208,
"Egzamin": "nie"
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak

Metoda: POST
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body:
{
"Nazwa": "Zarządzanie projektem informatycznym",
"ECTS": 2,
"Sala": 216,
"Egzamin": "nie"
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak

Metoda: POST
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body:
{
"Nazwa": "Zaawansowane technologie bazodanowe",
"ECTS": 3,
"Sala": 208,
"Egzamin": "nie"
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak

Metoda: POST
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body:
{
"Nazwa": "Technologie komponentowe i sieciowe",
"ECTS": 2,
"Sala": 208,
"Egzamin": "tak"
}
Odpowiedź:
HTTP Code: 200 OK
Body: brak
```

## 2. Pobranie wszystkich przedmiotów
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body:
[
    {
        "Id": 1,
        "Nazwa": "Metodologie obiektowe",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "tak"
    },
    {
        "Id": 2,
        "Nazwa": "Testowanie oprogramowania",
        "ECTS": 1,
        "Sala": 216,
        "Egzamin": "nie"
    },
    {
        "Id": 3,
        "Nazwa": "Technologie i aplikacje webowe",
        "ECTS": 3,
        "Sala": 208,
        "Egzamin": "nie"
    },
    {
        "Id": 4,
        "Nazwa": "Zarządzanie projektem informatycznym",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "nie"
    },
    {
        "Id": 5,
        "Nazwa": "Zaawansowane technologie bazodanowe",
        "ECTS": 3,
        "Sala": 208,
        "Egzamin": "nie"
    },
    {
        "Id": 6,
        "Nazwa": "Technologie komponentowe i sieciowe",
        "ECTS": 2,
        "Sala": 208,
        "Egzamin": "tak"
    }
]
```

## 3. Pobranie przedmiotów, które mają egzamin
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty?Egzamin=tak
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body:
[
    {
        "Id": 1,
        "Nazwa": "Metodologie obiektowe",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "tak"
    },
    {
        "Id": 6,
        "Nazwa": "Technologie komponentowe i sieciowe",
        "ECTS": 2,
        "Sala": 208,
        "Egzamin": "tak"
    }
]
```

## 4. Pobranie przedmiotów, które odbywają się w sali 216
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty?Sala=216
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body:
[
    {
        "Id": 1,
        "Nazwa": "Metodologie obiektowe",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "tak"
    },
    {
        "Id": 2,
        "Nazwa": "Testowanie oprogramowania",
        "ECTS": 1,
        "Sala": 216,
        "Egzamin": "nie"
    },
    {
        "Id": 4,
        "Nazwa": "Zarządzanie projektem informatycznym",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "nie"
    }
]
```

## 5. Pobranie przedmiotów które nie mają egzaminu i odbywają się w sali 208
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty?Egzamin=tak&Sala=208
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body:
[
    {
        "Id": 6,
        "Nazwa": "Technologie komponentowe i sieciowe",
        "ECTS": 2,
        "Sala": 208,
        "Egzamin": "tak"
    }
]
```

## 6. Pobranie przedmiotu o identyfikatorze 3
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty/3
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body:
{
    "Id": 3,
    "Nazwa": "Technologie i aplikacje webowe",
    "ECTS": 3,
    "Sala": 208,
    "Egzamin": "nie"
}
```

## 7. Pobranie przedmiotu o identyfikatorze 15
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty/15
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 404 Not Found
Body: brak
```

## 8. Usunięcie przedmiotu o identyfikatorze 2
```
Metoda: DELETE
Adres zasobu: http://localhost:8080/api/przedmioty/2
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 204 No Content
Body: brak
```

## 9. Pobranie wszystkich przedmiotów
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body:
[
    {
        "Id": 1,
        "Nazwa": "Metodologie obiektowe",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "tak"
    },
    {
        "Id": 3,
        "Nazwa": "Technologie i aplikacje webowe",
        "ECTS": 3,
        "Sala": 208,
        "Egzamin": "nie"
    },
    {
        "Id": 4,
        "Nazwa": "Zarządzanie projektem informatycznym",
        "ECTS": 2,
        "Sala": 216,
        "Egzamin": "nie"
    },
    {
        "Id": 5,
        "Nazwa": "Zaawansowane technologie bazodanowe",
        "ECTS": 3,
        "Sala": 208,
        "Egzamin": "nie"
    },
    {
        "Id": 6,
        "Nazwa": "Technologie komponentowe i sieciowe",
        "ECTS": 2,
        "Sala": 208,
        "Egzamin": "tak"
    }
]
```

## 10. Usunięcie wszystkich przedmiotów
```
Metoda: DELETE
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body: brak
```

## 11. Pobranie wszystkich przedmiotów
```
Metoda: GET
Adres zasobu: http://localhost:8080/api/przedmioty
Nagłówki: Content-Type: application/json
Request Body: brak
Odpowiedź:
HTTP Code: 200 OK
Body: []
```
