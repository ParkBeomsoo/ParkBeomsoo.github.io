---
layout: single
title:  "Elasticsearch  - Basic concepts"
categories: Elasticsearch
tag: [Elasticsearch, Search]
toc: true
author_profile: false
sidebar:
    nav: "docs"
#search: false
---

# Elasticsearch 기본개념 목차
<ul>
    <li>Elasticsearch란?</li>
    <li>Elasticsearch 특징</li>
    <li>Elasticsearch 기본 용어</li>
    <li>Elasticsearch의 장단점</li>
</ul>

## Elasticsearch란?
검색엔진의 시초인 루씬 (Lucene)을 기반으로 하고 있으며, 비정형 데이터를 색인하고 검색하는 것이 가능하며, 장점 중 하나인 역색인 구조를 사용하므로써 빠른 검색이 가능하다. 또한 분산 및 병렬처리, Restful API 제공 등 다양한 기능을 제공한다.
<ul>
  <li>비정형 데이터 : 정해진 규칙이 없는 데이터</li>
  <li>색인 : 문서에서 키워드를 찾아 보기 쉽도록  정렬 및 나열</li>
  <li>역색인 : 키워드를 통해  문서를 찾는 방식</li>
</ul>

## Elasticsearch 특징
ElasticSearch는 기본적으로 HTTP 통신을 통해 JSON 형식의 문서 단위로 저장하며, 문서는 인덱스 라는 논리적인 데이터베이스에 저장된다. 이렇게 저장된 데이터는 분산처리를 통해 실시간성으로 빠른 검색이 가능하다. 또한 검색엔진이지만 MongoDB 와 같은 대용량 스토리지로도 활용이 가능하다.

## Elasticsearch 기본 용어
1. Index : 관계형 데이터베이스에서 table과 같이 데이터를 저장하는 공간
2. Shard : 관계형 데이터베이스의 파티션과 같이 인덱스 내부에 색인된 데이터는 여러개의 파티션으로 구성
3. Document : 데이터베이스의 row와 같이 데이터가 저장되는 최소 단위( JSON 포맷으로 저장)
4. Field : 관계형 데이터베이스의 Column과 같이 문서를 구성하기 위한 속성
5. Mapping : 문서의 필드, 필드 속성을 정의하고 색인 방법을 정의

## Elasticsearch의 장단점
### 장점
- **오픈 소스 검색 엔진** : 아파치 재단의 루씬 (Lucene) 기반으로 개발된 오픈 소스 검색엔진이며, 활발한 커뮤니티로 끊임 없이 개선되고 발전되고 있다.
- **역색인** : 역색인 구조로 전체 문서가 아닌 단어가 포함된  특정 문서의 위치를 알아내어 빠른 결과를 찾을 수 있다.
- **통계분석** : 비정형 로그 데이터를 수집하여 통계 분석에 활용할 수 있으며, Kibana를 연결하면 실시간으로 로그를 분석하고 시각화할 수 있다.
- **Restful API** : HTTP기반의 RESTful를 활용하고 요청/응답에 JSON을 사용해 개발 언어, 운영체제, 시스템에 관계없이 다양한 플랫폼에서 활용이 가능하다.
- **Multi-teneancy** : 서로 상이한 인덱스일지라도 검색할 필드명만 같으면 여러 인덱스를 한번에 조회할 수 있다.
- **다양한 검색** : 불린 검색, 언어 분석, 지리적 위치 검색, 쿼리 문자열, 맞춤법 검사 등 다양한 검색 기능을 제공한다.

### 단점
- **Near Reail-Time** : 데 이터 저장 시점에 해당 데이터를 색인, 색인된 데이터는 1초 뒤에나 검색이 가능해져서 실시간으로 검색이 불가능하다. (내부적으로 커밋(commit), 플러쉬(Flush)와 같은 복잡한 과정을 거친다.)</li>
- **Transaction Rollback** 지원 X : 전체적인 클러스터의 성능 향상을 위해 비용 소모가 큰 롤백과 트랜잭션 기능이 없다.</li>
- **데이터 업데이트 X** : 업데이트 명령이 올 경우 기존 문서를 삭제하고 새로운 문서를 생성한다. 업데이트에 비해서 많은 비용이 들지만 이를 통해 불변성(Immutable)이라는 이점을 취한다.</li>