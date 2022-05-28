## Style and Innovation in the Collaboration Networks of Soviet Architects, 1920-1955

This repo contains data & additonal resources for my BA diploma project. **Abstract:**

> This paper is devoted to the analysis of collaboration networks among Soviet architects and the determinants of their consecration. I claim that the influence of power relations on the cultural production thoroughly analyzed by social scientists (Bourdieu, 1983; Mills, 1963) becomes especially pronounced in the context of totalitarian state regimes which cannot leave a single sphere of human life without exhibiting control over it and politicizing its subject (Arendt, 1973). The collaboration networks of Soviet architects (1920-1955) provide a fruitful context for this thesis as architecture was institutionalized along with the official style change in the beginning of 1930 and remained an important part of the state manifestation until the death of Joseph Stalin and the mass construction era (Groys, 2011; Khmelnitsky, 2007; Paperny, 1985). The data comes from the [“How old is this house” open project (2020)](https://kontikimaps.ru/how-old/saint-p?p=h-spb). The methods applied include the temporal network analysis techniques, PCA clustering, and multivariate adaptive regression splines (MARS) models. The key findings are that (1) the collaboration network becomes centralized in 1940 (with the largest component accounting for 62% of the vertices) and remained stable until 1960, while (2) the network positions occupied by architects are not important for the prediction of their success if the institutional power affiliation is controlled.

### Data

The data used for the analysis is presented in 2 files: **edge list.xlsx** and **vertex list.csv**. Though there are many variables in each of them, you may probably need only:
- The variables `from`, `to`, and `year_int` from the **edge list.xlsx** allow you to build the dynamic network object. Also, you can filter by `rebuild` column: if its value is 1, the building was created as a result of architects' efforts in different times. The variables `displayed_label` and `unified_address` stands for the precise description of what architects did together.
- **vertex list.csv**, obviously, contains vertex attributes, including (1) `first_year` and `last_year` (used as `onset` and `terminus` respectively in `ndtv` package), (2) institutional power affiliation, like `studio_head1936`, `board_member1940`, and `board_member1945`, (3) `birth_year`, (4) and the dependent variables used in MARS models, `total` (total number of architects' buildings protected by the goverment) and `leningrad_authors_n_mentions` (number of architects' mentions in the [**"Leningrad Architecture"** journal](https://spb-projects.ru/forum/viewtopic.php?f=22&t=4291&start=30), issues *1936-01* - *1950-03*).


### Networks

The other files present the network slice at 1940 (e.i., the network structure in 1940, **architects_1940.html**) and the dynamics of city's architects collaboration in the period between 1880 and 1965 (**architects' network in motion.html**).

The former was created using the elegant `networkD3` package. The tip I come up with while doing it is to include the network description as a separate image - it allows to avoid difficulties with `htmltools` and `htmlwidgets` packages (though I used them to write the displayed text in html file and cut it with the Scissors). Also, when creating similar documents, one should care about the displayed laybels: I failed to create a vertex tooltip (like in `visNetwork` package, for example) and put all the important information in a single line. The second file was knitted with `ndtv` package without any fancy decisions (nodes' size is set to degree centralization in each year, while the displayed labels are given in English, not Russian, because of encoding problems).

In both cases, the edges' info was not included. As the purpose is to show the network at its most important year of existence (1940) and the overall dynamics, such details do not seem necessary.


**p.s.** If you have any questions regarding the data, methods, or even the results - feel free to email me (artur-pecherskikh@yandex.ru).
