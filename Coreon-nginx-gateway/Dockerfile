FROM nginx:1.25-alpine

# 기본 default.conf 제거
RUN rm -f /etc/nginx/conf.d/default.conf

# 우리가 만든 설정으로 교체
COPY nginx.conf /etc/nginx/nginx.conf

# 컨테이너 내부 헬스체크 (ALB 헬스체크와 별개로 유용)
HEALTHCHECK --interval=10s --timeout=3s --retries=3 \
  CMD wget -qO- http://127.0.0.1/health || exit 1

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
