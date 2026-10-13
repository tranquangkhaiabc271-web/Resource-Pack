:- use_rendering(svgtree).

% ==============================================================
% 1. CÁC QUY TẮC CÚ PHÁP (GRAMMAR RULES)
% ==============================================================

% --- Cấp S'' (Cho câu hỏi Wh-) ---
s_double_bar(s_double_bar(C2, S_bar)) --> c2(C2), s_bar(S_bar).

% --- Cấp S' (Cho câu hỏi Yes/No) ---
s_bar(s_bar(C, S)) --> c(C), sentence(S).
s_bar(s_bar(C1, S)) --> c1(C1), sentence(S).

% --- Cấp S (Sentence) - Hỗ trợ cả câu có dấu chấm/dấu hỏi và không dấu ---
sentence(s(NP, VP)) --> noun_phrase(NP), verb_phrase(VP), ['.'].
sentence(s(NP, VP)) --> noun_phrase(NP), verb_phrase(VP), ['?'].
sentence(s(NP, VP)) --> noun_phrase(NP), verb_phrase(VP).

% --- Complementizers ---
c2(c2(NP)) --> noun_phrase(NP).
c1(c1(MOD)) --> modal(MOD).
c(c(PROG)) --> progressive(PROG).
c(c(TENSE)) --> tense(TENSE).
c(c(PERF)) --> perfect(PERF).

% --- Noun Phrase (NP) ---
noun_phrase(np(NAME)) --> name(NAME).
noun_phrase(np(NP1, and, NP2)) --> noun_phrase_single(NP1), [and], noun_phrase_single(NP2).
noun_phrase(np(DET, NOM)) --> determiner(DET), nominal(NOM).
noun_phrase(np(who)) --> [who].

noun_phrase_single(np(NAME)) --> name(NAME).
noun_phrase_single(np(DET, NOM)) --> determiner(DET), nominal(NOM).

determiner(det(ART)) --> article(ART).
determiner(det(DEM)) --> demonstrative(DEM).

% --- Nominal (NOM) ---
nominal(nom(ADVP, NOM)) --> adverb_phrase(ADVP), nominal(NOM).
nominal(nom(AP, NOM)) --> adjective_phrase(AP), nominal(NOM).
nominal(nom(N)) --> noun(N).

% --- Adverb Phrase (AdvP) & Adjective Phrase (AP) ---
adverb_phrase(advP(ADV)) --> adverb(ADV).
adjective_phrase(ap(A)) --> adjective(A).

% --- Prepositional Phrase (PP) ---
prepositional_phrase(pp(P, NP)) --> preposition(P), noun_phrase(NP).
prepositional_phrase(pp(P, N)) --> preposition(P), noun(N).
prepositional_phrase(pp(p(to), '•')) --> [to].

% ==============================================================
% VERB PHRASE (VP) RECURSION & STRUCTURES
% ==============================================================

% --- VP Adjuncts / PPs / NPs ở tầng ngoài cùng ---
verb_phrase(vp(VP_CORE, PP)) --> vp_core(VP_CORE), prepositional_phrase(PP).
verb_phrase(vp(VP_CORE, NP)) --> vp_core(VP_CORE), noun_phrase(NP).
verb_phrase(VP_CORE) --> vp_core(VP_CORE).

% --- Cấu trúc trợ động từ (Auxiliaries) ---
vp_core(vp(PASS, VP)) --> passive(PASS), vp_base(VP).
vp_core(vp(MOD, VP)) --> modal(MOD), vp_core(VP).
vp_core(vp(PERF, VP)) --> perfect(PERF), vp_core(VP).
vp_core(vp(PROG, VP)) --> progressive(PROG), vp_base(VP).
vp_core(vp(TENSE, VP)) --> tense(TENSE), vp_base(VP).

% Chuyển sang VP Base
vp_core(VP) --> vp_base(VP).

% --- VP Base (Động từ chính & Lồng nhánh dọc 1 con) ---
vp_base(vp(v(intrans(past(V))))) --> verb_intrans_past(V).
vp_base(vp(v(intrans(V)))) --> verb_intrans(V).

vp_base(vp(v(trans(past(V))), NP)) --> verb_trans_past(V), noun_phrase(NP).
vp_base(vp(v(trans(V)), NP)) --> verb_trans(V), noun_phrase(NP).

% Cấu trúc bị động (Passive Trace '∅')
vp_base(vp(vp(v(complex(V))), '∅', AP)) --> verb_complex(V), adjective_phrase(AP).
vp_base(vp(vp(v(trans(V))), '∅')) --> verb_trans_past(V).
vp_base(vp(v(trans(V)), '∅')) --> verb_trans_past(V).

% Cấu trúc hai tân ngữ (Ditransitive)
vp_base(vp(v(ditrans(V)), NP, PP)) --> verb_ditrans(V), noun_phrase(NP), prepositional_phrase(PP).

% ==============================================================
% 2. TỪ ĐIỂN (LEXICON)
% ==============================================================

name(name('Sam')) --> ['Sam'].
name(name('Max')) --> ['Max'].
name(name('Adrian')) --> ['Adrian'].
name(name('Millie')) --> ['Millie'].
name(name('Huy')) --> ['Huy'].
name(name('Otto')) --> ['Otto'].
name(name('Byron')) --> ['Byron'].
name(name('Oleg')) --> ['Oleg'].
name(name('Julia')) --> ['Julia'].

verb_intrans_past(sunbathed) --> [sunbathed].
verb_intrans(dance) --> [dance].
verb_intrans(dancing) --> [dancing].

verb_trans_past(studied) --> [studied].
verb_trans_past(fired) --> [fired].
verb_trans_past(arrested) --> [arrested].

verb_trans(having) --> [having].
verb_trans(filled) --> [filled].

verb_complex(driven) --> [driven].
verb_ditrans(give) --> [give].

progressive(prog(past(was))) --> [was].
progressive(prog(past(were))) --> [were].

passive(pass(pass(was))) --> [was].
passive(pass(pass(been))) --> [been].

modal(mod(pres(will))) --> [will].

modal(mod(past(would, not))) --> [would, not].

perfect(perf(have)) --> [have].
perfect(perf(pres(has))) --> [has].


tense(tense(past(did, not))) --> [did, not].
tense(tense(pres(does))) --> [does].

article(art(a)) --> [a].
article(art(the)) --> [the].
demonstrative(dem(this)) --> [this].

noun(n(stream)) --> [stream].
noun(n(conversation)) --> [conversation].
noun(n(morning)) --> [morning].
noun(n(pool)) --> [pool].
noun(n(tonight)) --> [tonight].
noun(n(menu)) --> [menu].
noun(n(boss)) --> [boss].
noun(n(noise)) --> [noise].
noun(n(pen)) --> [pen].

preposition(p(beside)) --> [beside].
preposition(p(by)) --> [by].
preposition(p(to)) --> [to].

adverb(adv(really)) --> [really].
adjective(a(tedious)) --> [tedious].
adjective(a(mad)) --> [mad].

