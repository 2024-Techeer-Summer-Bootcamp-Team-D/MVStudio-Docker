FROM golang:1.16 as build

# 작업 디렉토리 설정
WORKDIR /usr/src/rds_exporter

# 현재 디렉토리의 소스 코드를 컨테이너로 복사
COPY . .
COPY ./config.yml /usr/src/rds_exporter/config.yml

# 의존성 관리 도구를 사용하여 의존성 설치 및 애플리케이션 빌드
RUN go mod download
RUN CGO_ENABLED=0 go build -o /bin/rds_exporter

# 두 번째 단계: 최종 이미지 준비
FROM alpine:latest

# 빌드 단계에서 생성된 실행 파일을 최종 이미지로 복사
# COPY --from=build /bin/rds_exporter /bin/rds_exporter
COPY --from=build /bin/rds_exporter /bin/
COPY --from=build /usr/src/rds_exporter/config.yml /etc/rds_exporter/config.yml

RUN apk update && \
    apk add ca-certificates && \
    update-ca-certificates

EXPOSE      9042
ENTRYPOINT  [ "/bin/rds_exporter", "--config.file=/etc/rds_exporter/config.yml" ]
